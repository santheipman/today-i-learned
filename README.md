# today-i-learned

- 12/12/2023:
  - [AI] 3D pose estimation: 3D poses are usually extracted from 2D pose ground truth. The models that convert joints from 2D to 3D are relatively small (about hundreds of MBs). Useful sources include [this](https://mmpose.readthedocs.io/en/latest/user_guides/inference.html) and [this](https://motionbert.github.io/).
  - [SE][Testing] ([source](https://abseil.io/resources/swe-book/html/ch11.html)) Maintaining a test suite takes effort, but it brings several benefits, such as confidence when making changes in code, less time spent debugging, avoiding costly bugs, etc. Interestingly:
    - To be able to write tests easily, your code should also be modular.
    - Writing tests gives you a chance to be the user of your API. So, you can get a sense of where it might be challenging to use.
    - Test cases can serve as a form of documentation for the code. Moreover, when business changes occur, test cases often fail, allowing us to update them together with the code.
- 13/12/2023:
  - [SE] A valuable tip for identifying the cause of a bug is to employ the [5 Whys](https://en.wikipedia.org/wiki/Five_whys) recursively asking *why*.
  - [SE] ElasticSearch can be employed for log analytics, complemented by Kibana, a data visualization tool. Alongside success stories shared by ElasticSearch themselves [[1]](https://www.elastic.co/blog/what-the-oak-ridge-national-laboratory-learned-about-its-supercomputers-by-running-elastic)[[2]](https://www.elastic.co/blog/why-usgovernment-scaling-cybervisibility-elastic-cdm-cybersecurity-analyze-data) and positive feedbacks from a less biased community discussion [[3]](https://www.reddit.com/r/aws/comments/f00t52/eli5_when_should_one_use_elasticsearch_as_opposed/), engineering blogs from tech companies [[4]](https://www.uber.com/en-VN/blog/logging/) [[5]](https://posthog.com/blog/clickhouse-vs-elasticsearch) highlight alternative robust solutions like ClickHouse (Apache Druid is also mentioned, though it may be considered overkill for mere log analytics). The drawbacks of using ElasticSearch for log analytic tasks are primarily related to aggregation performance, and engineers must follow specific label value types, handle queries that are not in SQL, and encounter restrictions in Kibana charts when working with complex joins.
- 14/12/2023:
  - [Go] Today, I encountered a situation where I needed to log the value of an unexported field of a struct defined in a 3rd party package. `unsafe.Pointer` saved the day for me. You can read it in detail [here](./details/14_12_23.md).
- 17/12/2023:
  - [DB] In MongoDB, *Read Own Writes* refers to the ability to read the result of your previous write. If you read from the secondary replica, there's a chance that it hasn't replicated your write yet. Reading the documents, you might mistakenly believe that a read with a majority read concern following your write would be sufficient. A read with a majority read concern simply returns the in-memory view of the majority state of the data that a replica holds. In a scenario where a replica has not acknowledged your write, its majority view is also stale. You can read more about these in this awesome [blog post](https://vkontech.com/causal-consistency-guarantees-in-mongodb-majority-read-and-write-concerns/).
- 18/12/2023:
  - [SE] I 've seen a pattern for handling websocket connections in [Mattermost](https://github.com/mattermost/mattermost/blob/master/server/channels/app/platform/web_hub.go) and [Neffos](https://github.com/kataras/neffos/blob/e633b24d7aa1604eb9c9e614974bec6c4c64315d/server.go#L167-L207). What does is called? Web-Hub Pattern? Is it inspired from NodeJs's event loop? This week I'll explore more about it.