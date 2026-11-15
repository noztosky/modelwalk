# 8채널 NeoPixel LED 컨트롤러

5V 어댑터 1개로 NeoPixel(WS2812B 계열) 스트립 8줄(줄당 최대 256개)을 구동하고, 버튼 10개와 USB(PC)로 제어하는 수삽형 컨트롤러 보드.

## 문서

| 문서 | 파일 | 온라인 원본 |
| --- | --- | --- |
| 요구사항 정의서 | [PDF](docs/8채널_NeoPixel_LED_컨트롤러_요구사항_정의서.pdf) · [Word](docs/8채널_NeoPixel_LED_컨트롤러_요구사항_정의서.docx) | https://claude.ai/artifact/CFcufVQfo2Kfoy8Xig6gp6 |
| 제품 소개 및 조작 안내 (고객용) | [PDF](docs/8채널_LED_컨트롤러_제품소개_조작안내.pdf) | https://claude.ai/artifact/Du6iUqEBAMUfq2tAKUeiHQ |

## 구성 요약

- MCU: ESP32 DevKit (38핀, ESP32-WROOM-32E), 소켓 장착
- 레벨 변환: 74HCT245 ×1 (3.3V 직결 시 점퍼로 우회)
- 출력: 3P 단자대 ×8 (5V/DATA/GND), 채널별 PTC 퓨즈, 33Ω 직렬 저항
- 입력: 대전류 2P 단자대 + 2200µF, USB 전원은 쇼트키 다이오드로 분리
- 버튼: 택트 스위치 ×10 (GPIO34·35·39는 외부 10kΩ 풀업)
- PCB: 2층, 100×100mm 이내, 전부 스루홀 (JLCPCB PCB만 주문, 수삽)

## 핀 배정 (초안, 모듈 실물 확인 후 확정)

| 기능 | GPIO |
| --- | --- |
| LED1~8 데이터 | 16, 17, 18, 19, 21, 22, 23, 25 |
| SW1~10 | 26, 27, 32, 33, 13, 14, 4, 34, 35, 39 |

## 펌웨어

- 시제품 검증: [WLED](https://github.com/wled/WLED) (EUPL v1.2)
- 납품용: 자체 펌웨어 ([FastLED](https://github.com/FastLED/FastLED), MIT) + USB 시리얼 JSON 명령 + PC 프로그램
