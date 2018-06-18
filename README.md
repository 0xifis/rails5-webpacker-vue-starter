[Work in Progress]

_Written by: Vishnu R Menon_

# Software Versions
* Ruby ~> 2.5
* Node => 9.4.0
* Yarn ~> 1.3
* PostgreSQL ~> 9.6
* Rails ~> 5.2.0.rc1
* Geckodriver ~> 0.19
* Imagemagick ~> 7.0

# Setting up Development Environment
## Clone git repository from github
```
git clone git@github.com:vishthemenon/uteepi3.git
```

## Set rails secrets master key
```
cd uteepi3
echo <MASTER-KEY> >> config/master.key
```

## Start rails server
```
bundle install
yarn install
rails db:create
rails db:migrate
rails server
```

## Start webpack dev server
```
bin/webpack-dev-server
```

## Start development SMTP server to send/catch emails
```
gem install mailcatcher
mailcatcher
```

## Running tests
```
bin/rspec
```

# Git workflow (git-flow) 
* http://nvie.com/posts/a-successful-git-branching-model/
* https://jeffkreeftmeijer.com/git-flow/
## TL;DR
1. Work on your own feature branches
2. Send pull requests to develop branch
3. At the end of every week, develop is merged into master and prepared for release.

# Commit message style
Based on Chris Beams commit message style as written in his blog article - https://chris.beams.io/posts/git-commit/

* Separate subject from body with a blank line
* Limit the subject line to 50 characters
* Capitalize the subject line
* Do not end the subject line with a period
* Use the imperative mood in the subject line
* Wrap the body at 72 characters
* Use the body to explain what and why vs. how

## Good Example
```
Summarize changes in around 50 characters or less

More detailed explanatory text, if necessary. Wrap it to about 72 characters
or so. In some contexts, the first line is treated as the subject of the
commit and the rest of the text as the body. The blank line separating
the summary from the body is critical (unless you omit the body entirely);
various tools like `log`, `shortlog` and `rebase` can get confused if
you run the two together.

Explain the problem that this commit is solving. Focus on why you are
making this change as opposed to how (the code explains that). Are there
side effects or other unintuitive consequences of this change? Here's
the place to explain them.

Further paragraphs come after blank lines.
 - Bullet points are okay, too
 - Typically a hyphen or asterisk is used for the bullet, preceded by a
   single space, with blank lines in between, but conventions vary here

If you use an issue tracker, put references to them at the bottom,
like this:

Resolves: #123
See also: #456, #789
```

## Testing/Code Quality
To make sure your code passes CI, make sure the following runs without errors
1.  [Rubocop](https://github.com/bbatsov/rubocop)\* - Checks for ruby static code for ~~errors~~ offences. Run rubocop or rubocop -a if you are lazy and rather have rubocop auto fix the errors.
2.  [EsLint](https://github.com/eslint/eslint)\* - Checks for linting errors with Javascript Code. Uses [AirBnB's .eslintrc](https://github.com/airbnb/javascript). Requires yarn global add eslint@latest eslint-config-airbnb eslint-plugin-import eslint-plugin-jsx-a11y eslint-plugin-react 
3.  [Haml-Lint](https://github.com/brigade/haml-lint)\* - Check for linting error with Haml Code. Requires gem install haml-lint 
4.  [Sass-Lint](https://github.com/sasstools/sass-lint)\*† - Check for linting errors in SCSS Code. Requires yarn global add sass-lint 
5.  Tests - Make sure all tests have passed. Run bin/rspec. [Guard](https://github.com/guard/guard-rspec) has been set up for you so you can run guard (bin/guard) in another shell to watch for file changes and automatically run tests.
6.  [_Reek_](https://github.com/troessner/reek)_ - to detect _[_Code Smells_](https://blog.codeship.com/how-to-find-ruby-code-smells-with-reek/)
7.  _PENDING Setup _[_Brakeman_](https://brakemanscanner.org/)_ to detect security vulnerabilities_

> _\*All the linters are have plugins for the popular text editors (ie. Emacs, Sublime, Atom etc.). It's recommended to install them so that you can see the errors in realtime. The plugins should be able to detect the respective config files if you set the project directory in your editor._

> _†If you hate formatting your SCSS like me, check out [_CSScomb_](https://github.com/csscomb/csscomb.js). It has a CLI & plugins for the popular text editors to automatically format (ie. sort properties) your SCSS with a keystroke. The config file, `.csscomb.json` has been set up. It __should__ match the Sass-Lint config. If not, send start an issue and send in a pull request._

> _To attain maximum code zen, you could add git-hooks to ensure you have not messed up anything that might take you over. Some git-hooks have been configured for you using [_overcommit_](https://github.com/brigade/overcommit) in `.overcommit`. The git-hooks are not installed by deafult. If you like to use them (and you should, really), you will have to install overcommit gem with `gem install overcommit` and initiate it with `overcommit --install`._

![](https://storage.googleapis.com/slite-api-files-production/files/c3ae52e3-8774-4bf6-b0ba-434a4c84ec5f/image.png)
