# Guidelines

This is a collection of guidelines and background information for this project.

## Directory structure

  * the `bootstrap.cfg` in the root directory should be the only file meeded to be executed in order to load the framework

  * there should be no additional configuration files in the main directory if possible; create subdirectories for each new component

  * you may create more levels of subdirectories if it's sensible

  * the first level of an subdirectory located in the root directory should contain a file named `main.cfg`

    * This file can either contain code, more includes or both

    * the `main.cfg` should be the only file needed to be executed in order to load the component

      * Same goes for submodules if existing, but that does not mean that each subdirectory requires an `main.cfg`

      example:
      ```
      CFGO
      ├── bootstrap.cfg
      └── module
          ├── main.cfg
          ├── submodule0
          │   ├── includes
          │   │   └── incl0.cfg
          │   └── main.cfg
          └── submodule1
              └── main.cfg
      ```

## Documentation

Documentation is really important for this project. Not only for the users, but also for the maintainers and contributors.

The programming/scripting possibilities are very restricted, which sometimes requires complicated workarounds. This leads to code that is difficult to understand. Make use of comments and try to explain what you are doing.

  * use horizontal lines in a sensible way to structure larger comment blocks or to seperate  code

  * horizontal lines should be 80 characters wide (including comment symbols) smaller lines are also possible, but for bigger seperations, 80 charater wide lines should be used

  ```
  // -----------------------------------------------------------------------------
  ```

  * every config that is providing essential functions (not just loading additional scripts) should have a comment block in the beginning. It should include:

    * the config/script name

    * a summary of the features it implements and how to use them.

    * an interface section; relevant commands (aliases) for using the featues implementes.

      * Might sound redundant but see the example below. Basically an extensive list of commands that can be used (no commands that are just used internally to provide the function)

    * an option section; basically the same as the interface section, but with options that might be available.

      * e.g. customizable logging message

   example:

  ```
  // -----------------------------------------------------------------------------
  // My Function
  // -----------------------------------------------------------------------------
  //
  // Description:
  //
  // This script provides my awesome function.
  //
  //
  // Usage:
  //
  // You first must initialize this function:
  //
  //     cfgo_awsm_init
  //
  // Then you can use this function:
  //
  //     cfgo_awsm_run
  //
  // -----------------------------------------------------------------------------

  // --------------------------------- Interface ---------------------------------

  // init
  cfgo_awsm_init

  // run it
  cfgo_awsm_run
  cfgo_awsm_run2

  // status
  cfgo_awsm_stat

  // ---------------------------------- Options ----------------------------------

  // Messages output when running the function
  cfgo_awsm_msg "echo This is awesome"

  // -----------------------------------------------------------------------------

  // ... internal code
  <snip>
  ```

## Aliases
This project relies on aliases heavily.

  * the maximum length for aliases is 31 characters

  ```
  ] alias abcdefghijklmnopqwstuvwxyz12345 "test"
  ] alias abcdefghijklmnopqwstuvwxyz123456 "test
  Alias name is too long
  ```

  * to avoid name collisions, the prefix `cfgo` should be used

  * aliases should have a clear structure, you should be able to recognize which submodule they are part of

  ```
  // bad
  cfgo_hl
  cfgo_hl_b
  cfgo_load

  // better
  cfgo_out_hl
  cfgo_out_hl_b
  cfgo_cfg_load
  ```

  * because of the length restriction and for readability, you should still use simple variable, short aliases