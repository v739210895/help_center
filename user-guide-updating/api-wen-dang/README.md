# API Documentation

The system provides multiple built-in features for the game, which can be used to collect players' openid, notify the game in real-time after answering questions, distribute rewards, and more.

Self-service access can begin by filling out a survey[https://in.weisurvey.com/v2/?sid=5f589c6e76051fa2a616a549](https://in.weisurvey.com/v2/?sid=5f589c6e76051fa2a616a549)，Self-access according to the recommended scheme at the end of the volume; if you have any questions during the access process, please consult: IMUR survey system assistant.

{% hint style="info" %}
The process implementation and example introduction can be referred to[https://docs.qq.com/slide/DSlR6WExqemZub092](https://docs.qq.com/slide/DSlR6WExqemZub092)
{% endhint %}

![Introduction to Instance Process](<../../.gitbook/assets/image (134).png>)

### \[Appendix] API Documentation Directory

<table data-header-hidden><thead><tr><th width="231.5">场景</th><th>使用接口</th></tr></thead><tbody><tr><td>Scene</td><td>Using the interface</td></tr><tr><td>Collect the user's openid from embedded placement</td><td><a href="msdkv3-deng-lu-tai-cai-ji.md">MSDK-V3 Login State Collection</a>、<a href="msdkv5-deng-lu-tai-cai-ji.md">MSDK-V5 Login State Collection、</a><a href="intl-deng-lu-tai-cai-ji.md">INTL Login State Collection</a>、<a href="fei-msdk-deng-lu-tai-chuan-di-jie-kou.md">Parameter Passing Interface (Strict Validation Mode)</a>、<a href="parameter-transfer-interface-no-verification-mode.md">arameter Transfer Interface (Non-Verification Mode)</a><br></td></tr><tr><td><p>The developer's backend callback completes the answering user's openid, and passes through parameters, etc.</p><p>Used for awarding prizes, hiding survey buttons within the app, and other scenarios</p></td><td><a href="callback-interface.md">Callback Interface</a></td></tr><tr><td>After the user submits the survey, the survey system triggers the delivery of the AMS gift package.</td><td><a href="idip-fa-jiang.md">AMS Awards</a></td></tr></tbody></table>

