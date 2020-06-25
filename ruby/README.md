# Ruby Course

This is the **GitHub Actions configuration**. If you are looking for the **Stickler configuration**, you can find it [here](https://github.com/microverseinc/linters-config/tree/Stickler/ruby).

If you are not familiar with linters and GitHub Actions, read [root level README](../README.md).

## Set-up Rubocop GitHub Action

[Rubocop](https://www.rubocop.org/) is a Ruby static code analyzer (a.k.a. linter) and code formatter. It will enforce many of the guidelines outlined in the community [Ruby Style Guide](https://rubystyle.guide/).

This GitHub Action is going to run [Rubocop](https://docs.rubocop.org/en/stable/) to help you find style issues.

Please do the following **steps in this order**:

1. In the first commit of your feature branch create a `.github/workflows` folder and add a copy of [`.github/workflows/linters.yml`](.github/workflows/linters.yml) to that folder.
    - **Remember** to use the file linked above
    - **Remember** that `.github` folder starts with a dot.
2. **Do not make any changes in config files - they represent style guidelines that you share with your team - which is a group of all Microverse students.**
    - If you think that change is necessary - open a [Pull Request in this repository](../README.md#contributing) and let your code reviewer know about it.
3. When you open your first pull request you should see the result of the GitHub Actions:

![gh actions checks](../assets/images/gh-actions-rubocop-linters-checks.png)

Click on the `Details` link to see the full output and the errors that need to be fixed:

![gh actions failing checks](../assets/images/gh-actions-rubocop-failing-checks.png)

## [OPTIONAL]Set-up RSpec GitHub Action

You can run your tests with GitHub Actions to ensure that they are passing before merging a PR.

To use the GitHub Action to run your tests, please do the following **steps in this order**:

1. Add a copy of [`.github/workflows/tests.yml`](.github/workflows/tests.yml) to your `.github/workflows` folder.
    - **Remember** to use the file linked above
    - Do not modify or delete the [`.github/workflows/linters.yml`](.github/workflows/linters.yml) file that should already be in that folder.
    - RSpec by default will try to run any file ending in `_spec.rb` inside the `spec` folder. Make sure to follow this convention for your tests files so `rspec` can run your spec files.
    - You can modify the [`.github/workflows/tests.yml`](.github/workflows/tests.yml) file to better fit your custom needs.
3. When you open your pull request you should see the result of the GitHub Action:

![gh actions checks](../assets/images/gh-actions-rspec-tests-checks.png)

Click on the `Details` link of the test action to check the results of your tests.

## Set-up linters in your local env

### [RuboCop](https://docs.rubocop.org/en/stable/)

1. Add `gem 'rubocop', '~>0.81.0'` to `Gemfile` (not sure how to use Gemfile? Read [this](https://bundler.io/v1.15/guides/bundler_setup.html)).
2. Run `bundle install`.
3. Copy [.rubocop.yml](./.rubocop.yml) to the root directory of your project
4. **Do not make any changes in config files - they represent style guidelines that you share with your team - which is a group of all Microverse students.**
    - If you think that change is necessary - open a [Pull Request in this repository](../README.md#contributing) and let your code reviewer know about it.
5. Run `rubocop`.
6. Fix linter errors.
7. **IMPORTANT NOTE**: feel free to research [auto-correct options for Rubocop](https://rubocop.readthedocs.io/en/latest/auto_correct/) if you get a flood of errors but keep in mind that correcting style errors manually will help you to make a habit of writing a clean code!

### In case you use WSL (Windows Subsystem for Linux) for Windows 10 and there is some issues with executable path

1. Open the WSL on Visual Code (Ctrl + Shift + P) to bring it up the command palette and type in "default shell" and select WSL Bash 
    1.1. On the terminal tab check the dropdown menu on the right side and make sure you are on WSL
2. Add `gem install rubocop -v 0.81.0` (if you are getting some error such as "Carriage return character detected" run the command `gem install rubocop` 
3. Make sure the rubocop path on visual code is correct;
    3.1. Click in File > Preferences > Settings
    3.2. Look for `ruby-rubocop`
    3.3. If the Execute Path is empty run the command on WSL terminal `rbenv which rubocop` 
    3.4. After execute the command `which rubocop`
    3.5. Paste the output (e.g. /home/user/.rbenv/shims/rubocop) on the execute path
3. Copy [.rubocop.yml](./.rubocop.yml) to the root directory of your project
4. **Do not make any changes in config files - they represent style guidelines that you share with your team - which is a group of all Microverse students.**
    - If you think that change is necessary - open a [Pull Request in this repository](../README.md#contributing) and let your code reviewer know about it.
5. At the WSL terminal run the command `rubocop`.
6. Fix linter errors.
7. **IMPORTANT NOTE**: feel free to research [auto-correct options for Rubocop](https://rubocop.readthedocs.io/en/latest/auto_correct/) if you get a flood of errors but keep in mind that correcting style errors manually will help you to make a habit of writing a clean code!
