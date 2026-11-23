# How o1 Works

**답하기 전에 생각하는 데 계산을 쓰는 모델.** OpenAI o1은 모델을 키우는 대신, 답하기 전에 긴 사고 사슬(chain of thought)을 쓰도록 대규모 강화학습으로 학습했습니다. 그 결과 학습 시 계산(RL)과 테스트 시 계산(생각하는 시간) 양쪽에서 성능이 로그 스케일로 꾸준히 오릅니다. 「Learning to Reason with LLMs」(2024)와 「OpenAI o1 System Card」에서 **추론에 관한 부분**만 골라, 왜 생각을 적으면 더 풀리는지, 생각에 쓰는 계산을 늘리면 정확도가 어떻게 오르는지, 강화학습이 어떤 사고 습관을 만드는지를 브라우저에서 직접 실험해 보는 인터랙티브 교육 자료입니다.

🔗 **[데모 바로가기](https://dev-jonghoonpark.github.io/how-o1-works/)**

## 다루는 내용

1. **두 번째 스케일링 축** · train-time compute와 test-time compute, 사전학습 스케일링과의 비교
2. **토큰 한 칸의 계산 한도** · 바로 답하기 vs 중간 합을 적어 가며 답하기, 사고 사슬 = 출력을 작업 메모리로 쓰기
3. **o1 이전의 계보** · CoT 프롬프팅, Self-Consistency, STaR, Let's Verify Step by Step(PRM), 테스트 시 계산 최적 배분
4. **테스트 시 계산** · AIME 74 → 83 → 93%(pass@1 · 64개 다수결 · 1000개 재순위)를 재현하는 샘플링 시뮬레이터, 다수결과 채점기의 차이, pass@N 상한
5. **학습 시 계산** · 정답 보상만으로 "틀린 것 같으면 다시 시도"를 배우는 REINFORCE 장난감, 자기 점검 능력과 길이 벌점, DeepSeek-R1의 규칙 기반 보상과 aha moment
6. **사고 사슬 들여다보기** · o1-preview의 암호 해독 과정을 단계별로 다시 밟기, 같은 규칙으로 암호 만들기
7. **손으로 짠 전략 vs 스케일** · IOI 2024(156 → 213 → 362.14 → 395.64), Codeforces 레이팅
8. **사고 사슬을 숨긴 이유와 모니터링** · CoT 기만 모니터(0.17%), deliberative alignment, 탈옥·환각 평가, Apollo Research
9. **한계와 열린 질문** · 정리와 퀴즈 8문항

## 참고

- OpenAI (2024), *Learning to Reason with LLMs* — [openai.com](https://openai.com/index/learning-to-reason-with-llms/)
- OpenAI (2024), *OpenAI o1 System Card* — [arXiv:2412.16720](https://arxiv.org/abs/2412.16720)
- OpenAI (2025), *Competitive Programming with Large Reasoning Models* — [arXiv:2502.06807](https://arxiv.org/abs/2502.06807)
- Lightman et al. (2023), *Let's Verify Step by Step* — [arXiv:2305.20050](https://arxiv.org/abs/2305.20050)
- Snell et al. (2024), *Scaling LLM Test-Time Compute Optimally…* — [arXiv:2408.03314](https://arxiv.org/abs/2408.03314)
- DeepSeek-AI (2025), *DeepSeek-R1* — [arXiv:2501.12948](https://arxiv.org/abs/2501.12948)

[how-ai-works](https://github.com/dev-jonghoonpark/how-ai-works) 시리즈의 일부입니다.
