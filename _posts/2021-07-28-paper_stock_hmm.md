---
layout: post
title: paper-Stock Market Perdiction Using Hidden Markov Models(2012)
categories: [review]
tags: [paper,stock,hmm,finance]
---
책 "인공지능 투자자 퀀트"에서 언급되었길래 읽어보았다. 논문을 각잡고 읽어본 것은 처음인 것 같아서 조금 걱정했지만 쭉 훑어보니 짧고 간결한 내용의 논문이라 안심했다. (4page)
다만 모르는 영어단어가 있어서 이것저것 찾아보면서 읽느라 조금 오래걸린 점은 있다. 어차피 보면서 다이어리에도 정리하니까 여기에는 간단하게 적어봐야겠다.

는 수식을 적어야되는데 너무 귀찮다 그냥 거의 말로만 적어봐야지 

이 논문은 주식의 주가(Stock value)를 예측하는 방법으로 HMM(Hidden Markov Model)을 제시하고 있다.
HMM은 Markov Model과 유사하지만 상태 S<sub>t</sub>는 숨겨져 있고 그 State로 부터 관측되는 관측치 O<sub>t</sub>만 볼 수 있는 상태로 분석해보는 것이다.

HMM: λ = (π,A,B) 라는 수식이 논문에서 주어진다.
π는 한 state가 첫 시점 즉 t=1일 때 시작할 확률을 말하고
A는 transtition matrix로 한 state에서 다른 state로 넘어갈 확률을 담은 matrix이다.
B는 b<sub>t</sub>(O<sub>t</sub>)로 표현되며 j시점에 O<sub>t</sub>를 관찰할 확률이라고 할 수 있다. 
계산은 Baum-Welch algorithm으로 한다.

논문의 사례에서는 주식의 시가 종가 고가 저가의 4가지 데이터를 활용했으며 정보가 영향을 미치는 것이 latent(지연시간)이 10일이라고 가정해서
O<sub>t</sub>, O<sub>t</sub> ... O<sub>t</sub> 이 O<sub>t</sub>에 영향을 미치는 식으로 구성하여 예측했다.

논문 읽고 느낀점
- 별로 까다롭지 않은 모델인 것 같은데 생각보다 잘 맞춰서 놀랐다. 나는 lstm이 주가를 예측하는게 잘 안되는 걸 보고 아 이건 안되나 싶었는데 또 이런걸 보면 은근 잘맞추는 것 같다.
- 예시로 든 주식이 4종류인 것, 비교 대상이 최근 모델은 아닌 것 (사실 당연하다. 이 모델도 옛날거니까) 이 아쉽다. 다양한 주식에 적용해보면 어떨까 궁금하고 해보고 싶다.
- 논문 읽는게 그리 어렵진 않았다.
