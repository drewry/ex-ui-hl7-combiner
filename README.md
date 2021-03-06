# Example HL7 Combiner Tool
The purpose of this example app is to show how you can use the [fdns-ms-hl7-utils](https://github.com/cdcgov/fdns-ms-hl7-utils) and [fdns-ms-combiner](https://github.com/cdcgov/fdns-ms-combiner) services with a front-end interface built with [fdns-ui-react](https://github.com/cdcgov/fdns-ui-react) and [fdns-js-sdk](https://github.com/cdcgov/fdns-js-sdk). The use case for this example app is to take a raw [HL7](http://www.hl7.org) file and parse this file and format it into an Excel spreadsheet with assigned columns and rows. The assignment to these columns and rows is defined by a Message Mapping Guide (MMG) which is defined in a JSON configuration file. This can be used for onboarding Jurisdictions to ensure messages are being received with a standardized mapping format.

## Running Locally

### Before you start
You will need to have the following installed before getting up and running locally:

- Docker, [Installation guides](https://docs.docker.com/install/)
- Docker Compose, [Installation guides](https://docs.docker.com/compose/install/)
- **Windows Users**: This project uses `Make`, please see [Cygwin](http://www.cygwin.com/) for running commands in this README

This project was bootstrapped with [Create React App](https://github.com/facebookincubator/create-react-app).

You can find the most recent version of the Create React App guide [here](https://github.com/facebookincubator/create-react-app/blob/master/packages/react-scripts/template/README.md).

### Installation

This app is dependent on two FDNS NPM packages.

* [FDNS JS SDK](https://www.npmjs.com/package/fdns-js-sdk)
* [FDNS React UI](https://www.npmjs.com/package/fdns-ui-react)


Run `npm i` to install dependencies.

### Run

To start the background processes necessary, run docker compose to spin up `fdns-ms-combiner`, `fdns-ms-hl7-utils`, and `fdns-ms-object`, which are all needed to run this app:

    docker-compose up -d

To start the app:

    npm start

You should be able to visit `http://localhost:3000/` to view the dashboard.

You will also need to load the [mmg-example.json](./mmg-example.json) config using the [fdns-ms-combiner](https://github.com/cdcgov/fdns-ms-combiner) service.

```sh
curl -X POST \
  "http://localhost:8085/api/1.0/config/mmg-example" \
   -H "accept: application/json" \
   -H "Content-Type: application/json" \
   -d @mmg-example.json
```

To stop running the docker background images:

	docker-compose down

### Secure Mode

This app is able to run in a configuration where a OAuth 2.0 access token is needed before accessing the front-end such as with Foundation Services running with OAuth 2.0 enabled. You can pass the following environment variables to your Docker container:

- `SECURE_MODE=true` to run in the secure mode configuration
- `AUTH_URL=https://authorization-server.com/oauth/authorize` the value for the authorization URL from your OAuth 2.0 provider

## Public Domain
This repository constitutes a work of the United States Government and is not
subject to domestic copyright protection under 17 USC § 105. This repository is in
the public domain within the United States, and copyright and related rights in
the work worldwide are waived through the [CC0 1.0 Universal public domain dedication](https://creativecommons.org/publicdomain/zero/1.0/).
All contributions to this repository will be released under the CC0 dedication. By
submitting a pull request you are agreeing to comply with this waiver of
copyright interest.

## License
The repository utilizes code licensed under the terms of the Apache Software
License and therefore is licensed under ASL v2 or later.

The source code in this repository is free: you can redistribute it and/or modify it under
the terms of the Apache Software License version 2, or (at your option) any
later version.

The source code in this repository is distributed in the hope that it will be useful, but WITHOUT ANY
WARRANTY; without even the implied warranty of MERCHANTABILITY or FITNESS FOR A
PARTICULAR PURPOSE. See the Apache Software License for more details.

You should have received a copy of the Apache Software License along with this
program. If not, see https://www.apache.org/licenses/LICENSE-2.0.html

The source code forked from other open source projects will inherit its license.


## Privacy
This repository contains only non-sensitive, publicly available data and
information. All material and community participation is covered by the
Surveillance Platform [Disclaimer](https://github.com/CDCgov/template/blob/master/DISCLAIMER.md)
and [Code of Conduct](https://github.com/CDCgov/template/blob/master/code-of-conduct.md).
For more information about CDC's privacy policy, please visit [http://www.cdc.gov/privacy.html](http://www.cdc.gov/privacy.html).

## Contributing
Anyone is encouraged to contribute to the repository by [forking](https://help.github.com/articles/fork-a-repo)
and submitting a pull request. (If you are new to GitHub, you might start with a
[basic tutorial](https://help.github.com/articles/set-up-git).) By contributing
to this project, you grant a world-wide, royalty-free, perpetual, irrevocable,
non-exclusive, transferable license to all users under the terms of the
[Apache Software License v2](https://www.apache.org/licenses/LICENSE-2.0.html) or
later.

All comments, messages, pull requests, and other submissions received through
CDC including this GitHub page are subject to the [Presidential Records Act](https://www.archives.gov/about/laws/presidential-records.html)
and may be archived. Learn more at [https://www.cdc.gov/other/privacy.html](https://www.cdc.gov/other/privacy.html).

## Records
This repository is not a source of government records, but is a copy to increase
collaboration and collaborative potential. All government records will be
published through the [CDC web site](https://www.cdc.gov).

## Notices
Please refer to [CDC's Template Repository](https://github.com/CDCgov/template)
for more information about [contributing to this repository](https://github.com/CDCgov/template/blob/master/CONTRIBUTING.md),
[public domain notices and disclaimers](https://github.com/CDCgov/template/blob/master/DISCLAIMER.md),
and [code of conduct](https://github.com/CDCgov/template/blob/master/code-of-conduct.md).
