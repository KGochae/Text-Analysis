**WAKTAVERSE dashboard** 에서 이용하기 위해 학습시킨 자연어처리(이진분류) 모델 입니다.

## 요약
### 데이터

> * 한국어 단발성 대화 
> * [한국어 악성댓글 데이터](https://github.com/ZIZUN/korean-malicious-comments-dataset) 
욕설이 들어갔거나, 강한 혐오표현, 비난
> * [욕설 감지 데이터셋](https://github.com/2runo/Curse-detection-data) 
> 단순 욕설, 인종 차별적인 말, 정치적 갈등을 조장하는 말, 성적·성차별적인 말, 타인을 비하하는 말, 그 외에 불쾌감을 주거나 욕설로 판단되는 말 
> * 유투브 댓글을 수집하여 일부 라벨링

### 데이터 결합
> 댓글이 clean(긍정적)인지, 부정적인지 이진분류 하는데에 초점을 맞췄기 때문에, '부정'중에 좀 더 세부적으로 라벨링('인종차별','성별혐오','단순악플' 등)이 되어있는 데이터들을 모두 '부정'으로 합쳐주었습니다. 

긍정으로 라벨링된 데이터가 약 2만개 더 많습니다.

sentiment 긍정(1) : 125585 \
sentiment 부정(0) : 104299

![](https://velog.velcdn.com/images/liveandletlive/post/28675be5-44ad-4b54-9a6f-1a20a9de1bae/image.png)

### 전처리, tokenizer 모델
일부 인터넷 용어들 사전을 따로 만들어주기위해 커스텀하기 쉬운 ckonlpy로 선정 
* ckonlpy

### 학습모델
*  LSTM, Bilstm

### 전처리
> 딥러닝을 이용한 [자연어 처리 입문](https://wikidocs.net/book/2155)의 내용을 바탕으로 진행하였습니다.

### 모델요약

|model|accuracy|loss|
|---|---|---|
|LSTM|0.8471|0.36|
|BiLSTM|0.8497|0.37|

### TEST
각각의 accuracy, loss 값의 큰차이는 없지만 새로운 댓글들로 여러번 TEST 했을 때  BiLSTM 모델이 더 잘 분별하여 해당 모델을 WAKTAVERSE DASHBOARD 에 적용시켰습니다.

![image](https://github.com/KGochae/Youtube/assets/86241587/f9b411a5-016e-4f7b-a06e-f69c76a157f2)

> * '_고세구 팬 수준 ㅋㅋ 그러니까 시청자 꼴지지 ....'_ , '_왜이렇게 어수선해요 ㅋㅋㅋ' , '틀딱 둘기인데 마니또가 뭔가요ㅜㅜ'_ 같이 부정적이거나 딱히 감정이 들어가있지 않은 혼잣말, 질문유형 같은 중립적인 문장에 낮은 score를 주었습니다.
> * 대체적으로 부정적이나 중립적이다고 판단한 댓글의 경우는 확연하게 분류하지는 못했지만 확실하게 긍정적인 댓글을 긍정적으로 예측한 경우가 많았습니다. 

---

* 좀 더 자세한 내용은 [velog](https://velog.io/@liveandletlive/%EA%B8%B0%EB%A1%9D5.-%EC%98%81%EC%83%81%EC%9D%98-%EB%8C%93%EA%B8%80)을 통해서 보실 수 있습니다!


