# Pine Player 플레이어 팩

Pine Player 가 새 음악 앱을 다루는 법을 적어 둔 **값(JSON)** 저장소다. 실행 코드는 들어 있지 않고, 앱은 이 값만 읽는다.

- 팩 하나 = `packs/<id>.json`. `id` `nameKo` `packageName` `tier` `capabilities` `automation` 이 뼈대다. `capabilities` 에는 **실기기에서 확인한 기능만** 적고, 후보는 `pendingCapabilities` 에 둔다.
- `automation` 은 `{"type":"none"}` 이거나 `{"type":"recipe","recipes":{...}}` 다. 레시피 단계는 launch / waitFor / click / setText / scrollUntil / ifPresent / confirm / back / fail / done 열 가지뿐이다.
- `catalog.json` 이 팩 목록이다. 항목마다 `url` 과 `sha256` 이 있고, 앱은 HTTPS 로 받아 해시가 맞을 때만 설치한다.
- 설치: 앱 설정 → 플레이어 → "팩 받기" 에서 목록을 보고 고르면 `filesDir/players/<id>.json` 에 저장된다. 삭제도 같은 화면에서 한다.
- 팩을 고쳤으면 `version` 을 올리고 `shasum -a 256 packs/<id>.json` 값을 `catalog.json` 에 다시 적는다. 판이 낮은 팩은 앱이 무시한다.

## 라이선스

MIT. `LICENSE` 참고.
