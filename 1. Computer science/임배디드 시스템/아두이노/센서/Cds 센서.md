---
tags:
  - 아두이노
  - 임베디드시스템
  - ComputerScience
---

[[전압분배공식]]

CD (CDS, Cadmium Sulfide) 센서는 빛의 강도나 조도를 측정하는 데 사용되는 광학 센서의 한 유형입니다. 이 센서는 빛의 양에 따라 전기 저항이 변화하는 특성을 활용합니다. CDS 센서는 주로 조도 센서 또는 광 감지기로 알려져 있으며 다양한 응용 분야에서 사용됩니다. 다음은 CDS 센서의 주요 특징과 작동 원리에 대한 설명입니다:

1. **작동 원리**:
    
    - CDS 센서는 반도체 소재인 카드뮴 황(CdS)을 사용합니다. 이 소재는 빛에 노출될 때 전기 저항이 변화합니다. **빛이 강해질수록 카드뮴 황의 [[전기 저항]]이 낮아지고, 빛이 약해질수록 전기 저항이 높아집니다.**

1. **조도 측정**:
    
    - CDS 센서는 주로 주변 환경의 조도 레벨을 측정하는 데 사용됩니다. 이것은 주변의 밝기 또는 어두움을 감지하고 조절해야 하는 응용 분야에 유용합니다. 예를 들어, 자동 조명 제어, 환경 모니터링 및 광학 장치의 조도 조절에 사용됩니다.

1. **응용 분야**:
    
    - 자동차의 라이트 센서: 자동차의 야간 주행 중 라이트를 자동으로 켜고 끄는 데 사용됩니다.
    - 조명 및 환경 제어: 건물 내부 밝기를 자동으로 조절하고 에너지를 절약하는 데 사용됩니다.
    - 카메라 조리개 제어: 디지털 카메라나 DSLR 카메라에서 조리개의 조절에 사용됩니다.
    - 일광량 측정: 일광량을 측정하여 태양 전지의 효율성을 평가하는 데 사용됩니다.

1. **장점**:
    
    - 비용 효율적이며 간단한 구조를 가집니다.
    - 적응력이 뛰어나 다양한 환경에서 사용 가능합니다.
    - 빠른 응답 시간을 가질 수 있습니다.

1. **제한 사항**:
    
    - 주변 온도 및 습도 변화에 민감할 수 있으며, 정확성이 영향을 받을 수 있습니다.
    - 극단적인 조건에서는 정확한 측정이 어려울 수 있습니다.


CDS 센서는 다양한 응용 분야에서 빛의 강도나 조도를 측정하고 모니터링하기 위한 간단하면서도 효과적인 도구로 사용됩니다.


![[Pasted image 20231011180255.png]]

# 실습코드

```cpp

const int CdsPin=0;
const int ledPin=13;
void setup() {
  // put your setup code here, to run once:
 Serial.begin(9600); 
 pinMode(13,OUTPUT);
}

void loop() {
  // put your main code here, to run repeatedly:
  int adcValue;
  int illuminance;

  adcValue=analogRead(CdsPin);
  illuminance=map(adcValue,0,1023,0,100);
  if(illuminance>50)
  {
    digitalWrite(ledPin,HIGH);
  }else
  {
    digitalWrite(ledPin,LOW);
  }
 
  Serial.println(illuminance);
  delay(500);
}

```