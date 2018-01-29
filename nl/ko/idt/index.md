---

copyright:
  years: 2017
lastupdated: "2017-11-02"

---
{:new_window: target="_blank"}  
{:shortdesc: .shortdesc}  
{:screen: .screen}  
{:codeblock: .codeblock}  
{:pre: .pre}  

# {{site.data.keyword.dev_cli_short}}
{: #developercli}	

{{site.data.keyword.dev_cli_long}}은 `dev` 플러그인을 사용하여 웹 프로젝트를 작성하고 개발하고 배치할 수 있는 확장 가능한 명령 중심 접근법을 제공합니다. 엔드-투-엔드 마이크로서비스 애플리케이션을 개발하기 위해 명령행 제어를 사용하고자 하는 개발자에게 적합합니다. 

{: shortdesc}

{{site.data.keyword.dev_cli_notm}}은 애플리케이션 빌드 및 테스트를 위해 두 개의 컨테이너를 사용합니다. 첫 번째는 애플리케이션을 빌드하고 테스트하기 위한 필수 유틸리티가 포함된 도구 컨테이너입니다. 이 컨테이너에 대한 Dockerfile은 [`dockerfile-tools`](#command-parameters) 매개변수에 의해 정의됩니다. 이는 일반적으로 특정 런타임의 개발에 유용한 도구를 포함하고 있으므로 개발 컨테이너라 생각할 수도 있습니다. 

두 번째 컨테이너는 실행 컨테이너입니다. 이 컨테이너는 {{site.data.keyword.Bluemix}} 등에서 사용할 수 있도록 배치하는 데 적합한 양식입니다. 그 결과, 애플리케이션을 시작하는 시작점이 정의됩니다. {{site.data.keyword.dev_cli_short}}을 통해 애플리케이션을 실행하도록 선택하면 이 플러그인은 이 컨테이너를 사용합니다. 이 컨테이너에 대한 Dockerfile은 [`dockerfile-run`](#run-parameters) 매개변수에 의해 정의됩니다. 


## {{site.data.keyword.dev_cli_notm}} 추가
{: #add-cli}


### 전제조건
{: #prereq}

{{site.data.keyword.dev_cli_short}}은 보완 기술 활용을 위해 고도로 확장 가능하므로 이를 완전히 탐색하고 올바르게 이용하기 위한 몇 가지 전제조건을 확보해야 합니다. 

<!--1. Install the [Cloud Foundry CLI ![External link icon](../icons/launch-glyph.svg "External link icon")](https://github.com/cloudfoundry/cli#getting-started "External link icon").-->

1. [{{site.data.keyword.Bluemix}} CLI ![외부 링크 아이콘](../icons/launch-glyph.svg "외부 링크 아이콘")](http://clis.ng.bluemix.net/ui/home.html)를 설치하십시오. 

2. [{{site.data.keyword.Bluemix_notm}}](https://www.bluemix.net) ID를 확보하십시오. 

3. 로컬로 애플리케이션을 실행하고 디버그하려면 [Docker ![외부 링크 아이콘](../icons/launch-glyph.svg "외부 링크 아이콘")](https://www.docker.com/get-docker)도 설치해야 합니다. 


### 시작하기 전에
{: #before-install}

1. [{{site.data.keyword.Bluemix_notm}} 지역](/docs/overview/whatisbluemix.html#ov_intro_reg)의 API 엔드포인트에 연결하십시오. 예를 들어, {{site.data.keyword.Bluemix_notm}} 미국 남부 지역에 연결하려면 다음 명령을 입력하십시오. 

	```
	bx api https://api.ng.bluemix.net
	```
	{: codeblock}
	
2. IBM ID 및 비밀번호를 입력하여 {{site.data.keyword.Bluemix_notm}}에 로그인하십시오. 

	```
	bx login
	```
	{: codeblock}
	
	**참고:**  신임 정보가 거부된 경우에는 사용자가 연합 ID를 사용 중일 수 있습니다. 연합 ID를 사용하여 인증하려면 다음 단계를 따르십시오. 
	
	<!-- 
	POINT TO IBM CLOUD CLI LOG IN DOCUMENTATION !!!
	
	This link does not work in production yet --> 
	
	1. [{{site.data.keyword.iamshort}} ![외부 링크 아이콘](../icons/launch-glyph.svg "외부 링크 아이콘")](https://www.bluemix.net/iam/#/apikeys){: new_window}에 로그인하십시오. 
	2. **API 키 작성**을 선택하십시오. 
		* apiKey 이름 및 설명을 입력하십시오. 
	3. apiKey를 다운로드하십시오. 
	4. 파일을 열고 `apiKey` 필드에서 값을 복사하십시오. 
	5. 다음 명령을 사용하여 로그인하십시오. 
	 
		```
		bx login --apikey <value>
		```
		{: codeblock}


### 설치
{: #installation}

1. 다음 명령을 실행하여 [{{site.data.keyword.dev_cli_short}} ![외부 링크 아이콘](../icons/launch-glyph.svg "외부 링크 아이콘")](/docs/cli/reference/bluemix_cli/index.html#install_plug-in){: new_window}을 설치하십시오. 
 
	```
	bx plugin install dev
	```
	{: codeblock}

2. 	다음 명령을 실행하여 플러그인 설치의 유효성 검증을 하십시오.   
 
	```
	bx dev
	```
	{: codeblock}


