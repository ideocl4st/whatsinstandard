# 이게 대체 뭐하는 사이트죠?
새로 매직: 더 개더링을 시작하시는 분들을 위해 스탠다드가 무엇인지, 그리고 언제 어떻게 세트가 제외되고 발매되는지 설명하기 위해 만들어진 사이트인 [What's in Standard?][website]를 한국어로 번역한 웹사이트입니다.

원본 웹사이트에 추가 언어를 지원하기 위한 토의가 진행되고 있긴 한데, 매직 아레나를 계기로 매직: 더 개더링을 시작하는 플레이어는 늘고 있지만 한국어 공식 홈페이지에 7월 30일 기점으로 코어 2019가 스탠다드 범위에 갱신되지 않은 모습을 보니 너무 슬픈 나머지 빠르게 번역 작업을 해서 웹사이트를 만들게 되었습니다.

오타, 비문 등이 있는 문장, 더 이해하기 쉬운 문장이나 원래 사이트에 없지만 있으면 좋겠다 싶은 설명을 위한 제안도 부탁드립니다. 다만 제가 프로그래머는 아니라서 뭔가 멋진 기능을 만드는 것은 불가능할 것 같네요. 양해 부탁드립니다.

To the original maintainer: I will be more than glad to help with the Korean translation of the original *[What's in Standard?][website]* website once it is ready for multi-language support. Please contact me if you need my help!

[밑은 원본 웹사이트의 README.md 내용입니다. 특별히 뺄 필요는 없으니 그대로 두도록 하겠습니다.]

# What's in Standard?
*[What's in Standard?][website]* is a simple reference page made to help new (or not new) Magic: The Gathering players easily
check which sets are currently in [Standard][standard-official], see when the next rotation is going to happen, and understand how
rotations work.

[website]: https://whatsinstandard.com/
[standard-official]: http://magic.wizards.com/en/content/standard-formats-magic-gathering 

## Development
### Dependencies
- [npm][npm]

[npm]: https://github.com/npm/npm

### Running it locally
```sh
git clone git@github.com:glacials/whatsinstandard
cd whatsinstandard
npm install
npm start
```

Then open [localhost:8080][localhost] in your browser!

[localhost]: http://localhost:8080

### Updating Set Information
If you're looking to add, remove, or change a set, you'll want to change [`api/internal.json`][api-internal] then run
```sh
npm install
```
to regenerate the API. This file is the source of truth for set information, as the website itself consumes the APIs
generated from this file.

[api-internal]: api/internal.json

#### Tests
The API has a few tests. You can run them with

```sh
npm test
```

To autorun them whenever test files update, use

```sh
npm run autotest
```

### Tech
*What's in Standard?* uses [Vue.js][vue], a lightweight JavaScript framework. It fetches the setlist from its own API
and filters it based on release and drop dates.

[vue]: https://vuejs.org/

### API
We've got an API. It's super slim and the output is written by hand but it works like a charm.

#### [/api/v5/sets.json][api]
This is the only API call we have. It returns something like this:

```json
{
  "deprecated": false,
  "sets": [
    {
      "name": "Battle for Zendikar",
      "block": "Battle for Zendikar",
      "code": "BFZ",
      "enter_date": "2015-10-02T00:00:00.000Z",
      "exit_date": "2017-09-29T00:00:00.000Z",
      "rough_exit_date": "Q4 2017"
    },
    ...,
  ]
{
```

The array is guaranteed to contain all sets currently in Standard, but also contains recently dropped sets and some
future sets. For API details including how to filter them, see [the API readme][api-readme].

[api]: https://whatsinstandard.com/api/v5/sets.json
[api-readme]: https://github.com/glacials/whatsinstandard/blob/master/api

## Attributions
Thanks to:

* For SVG set icon images:
  * BaconCatBug
  * White Dragon
  * Goblin Hero
  * Skibulk
  * Baka-Neku
  * Qanadhar
  * Poopski
* For gathering them: [jninnes][jninnes]
* For favicon: Nils Enevoldsen

[jninnes]: https://github.com/jninnes/mtgicons
