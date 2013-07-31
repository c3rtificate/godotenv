# GoDotEnv [![wercker status](https://app.wercker.com/status/507594c2ec7e60f19403a568dfea0f78 "wercker status")](https://app.wercker.com/project/bykey/507594c2ec7e60f19403a568dfea0f78)

A Go (golang) port of the Ruby dotenv project (which loads env vars from a .env file)

From the original Library:

> Storing configuration in the environment is one of the tenets of a twelve-factor app. Anything that is likely to change between deployment environments–such as resource handles for databases or credentials for external services–should be extracted from the code into environment variables.
> 
> But it is not always practical to set environment variables on development machines or continuous integration servers where multiple projects are run. Dotenv load variables from a .env file into ENV when the environment is bootstrapped.

## Installation

```shell
go get github.com/joho/godotenv
```

## Usage

Add your application configuration to your `.env` file in the root of your project:

```shell
S3_BUCKET=YOURS3BUCKET
SECRET_KEY=YOURSECRETKEYGOESHERE
```

Then in your Go app you can do something like

```go
import (
    "github.com/joho/godotenv"
    "os"
)

err := godotenv.Load()
if err != nil {
  os.Fatal("Error loading .env file")
}

s3Bucket := os.Getenv("S3_BUCKET")
secretKey := os.Getenv("SECRET_KEY")
```

While `.env` in the project root is the default, you don't have to be constrained

```go
_ := godotenv.Load("somerandomfile")
_ := godotenv.Load("filenumberone.env", "filenumbertwo.env")
```

Are all valid options

## Contributing

Contributions are most welcome! The parser itself is pretty stupidly naive and I wouldn't be surprised if it breaks with edge cases.

*code changes without tests will not be accepted*

1. Fork it
2. Create your feature branch (`git checkout -b my-new-feature`)
3. Commit your changes (`git commit -am 'Added some feature'`)
4. Push to the branch (`git push origin my-new-feature`)
5. Create new Pull Request

## CI

[![wercker status](https://app.wercker.com/status/507594c2ec7e60f19403a568dfea0f78/m "wercker status")](https://app.wercker.com/project/bykey/507594c2ec7e60f19403a568dfea0f78)

## Who?

The original library [dotenv](https://github.com/bkeepers/dotenv) was written by [Brandon Keepers](http://opensoul.org/), and this port was done by [John Barton](http://whoisjohnbarton.com) based off the tests/fixtures in the original library.