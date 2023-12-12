# today-i-learned

- 12/12/2023:
  - [AI] 3D pose estimation: 3D poses are usually extracted from 2D pose ground truth. The models that convert joints from 2D to 3D are relatively small (about hundreds of MBs). Useful sources include [this](https://mmpose.readthedocs.io/en/latest/user_guides/inference.html) and [this](https://motionbert.github.io/).
  - [SE] Maintaining a test suite takes effort, but it brings several benefits, such as confidence when making changes in code, less time spent debugging, avoiding costly bugs, etc. Interestingly:
    - To be able to write tests easily, your code should also be modular.
    - Writing tests gives you a chance to be the user of your API. So, you can get a sense of where it might be challenging to use.
    - Test cases can serve as a form of documentation for the code. Moreover, when business changes occur, test cases often fail, allowing us to update them together with the code.