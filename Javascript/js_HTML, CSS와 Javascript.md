## HTML / CSS / JAVASCRIPT 

1. DOM

    - DOM ? 웹 페이지에 대한 인터페이스로, 기본적으로 여러 프로그램들이 페이지의 콘텐츠 및 구조, 스타일을 읽고 조작할 수 있도록 API를 제공한다. 

    - 웹 브라우저가 띄어지는 순서

        1. 웹 브라우저가 원본 HTML 문서를 읽어들인 후, 스타일을 입히고 대화형 페이지로 만들어 뷰 포트에 표시하기의 과정을 Critical Rendering Path라고 한다.

            1-1. 브라우저는 읽어들인 문서를 파싱하여, 최종적으로 어떤 내용을 페이지에 렌더링 할지 결정

                2. 렌더 트리가 생성되고, 이 렌더트리는 웹 페이지에 표시될 HTML 요소들과 이와 관련된 스타일 요소들로 구성된다. 

                3. 브라우저는 렌더 트리를 생성하기위해 다음과 같은 두 모델이 필요하다

                    - DOM (DOCUMENT OBJECT MODEL) - html 요소들의 구조화된 표현

                    - CSSOM(CASCADING STYLE SHEETS OBJECT MODEL) - 요소들과 관련된 스타일 정보의 구조화된 표현

            1-2. 브라우저는 해당 렌더링을 수행한다.

    - DOM은 어떻게 생성 될까?

        - DOM은 원본 HTML 문서의 객체 기반 표현 방식이다. 둘은 서로 비슷하지만, DOM이 갖고 있는 근본적인 차이는 단순 텍스트로 구성된 HTML 문서의 내용과 구조가 객체 모델로 변환되어 다양한 프로그램에서 사용될 수 있다.

        - DOM의 객체 구조는 "노드 트리"로 표현된다. 하나의 부모 줄기가 여러 개의 자식 나뭇가지를 갖고, 또 각각의 나뭇가지는 잎들을 가질 수 있는 나무와 같은 구조로 이루어져 있다.

                    <html>
                        <head>
                            <title></title>
                        </head>
                        <body>
                            <h1></h1>
                            <p></p>
                        </body>
                    </html>

                    html - head - title - text

                    html - body - h1 - text
                    
                    html - body - p - text
                    
    - DOM이 아닌 것

        1. DOM은 HTML이 아니다.

            - DOM 은 HTML 문서로부터 생성되지만, 항상 동일하지 않다. DOM이 원본 HTML 소스와 다를 수 있는 두 가지 case가 있다.

                1. 작성된 HTML 문서가 유효하지 않을 때

                - DOM은 유효한 HTML 문서의 인터페이스 입니다. DOM을 생성하는 동안, 브라우저는 유효하지 않은 HTML 코드를 올바르게 교정합니다.

                            <html>
                                Hello, World! 
                            </html>

                            //에서 html 규칙의 필수 사항인 head 와 body 가 빠져있다. 그렇지만 생성된 DOM 트리에는 올바르게 교정되어 나타난다.

                            html - head
                            html - body - Hello,World!

                2. JS에 의해 DOM 이 수정될 때

                - DOM은 HTML 문서의 내용을 볼 수 있는 인터페이스 역할을 하는 동시에 동적 자원이 되어 수정될 수 있습니다.
                
                - 예를 들어, 자바스크립트를 사용해 DOM에 새로운 노드를 추가할 수 있습니다.

                            let newParagraph = document.createElement("p");
                            let paragraphContent = document.createaTextNode("I'm New!");
                            newParagrah.appendChild(paragraphContent);
                            document.body.appendChild(newParagraph);

                            // 이 코드는 DOM을 업데이트 한다. 하지만, HTML 문서의 내용을 변경하지는 않는다.

        2. DOM 은 브라우저에서 보여지는 것이 아니다.

            - 브라우저 뷰 포트에 보여지는 것은 렌더트리로, DOM 과 CSSOM의 조합이다. 

            - 렌더 트리는 오직 스크린에서 그려지는 것으로 구성되어 있어 DOM과 다르다.

            - 렌더링 되는 요소만 관련되어 있기 때문에, 시각적으로 보이지 않는 요소는 제외된다.

                        <html>
                            <head></head>
                            <body>
                                <h1>HEllo, World</h1>
                                <p style="display:none">How are you?</p>
                            </body>
                        </html>

                        // DOM 은 P 요소를 포함시킨다!

                        html - head
                        html - body - h1 - Hello,World!
                        html - body - p - How are you ?

                        // 렌더트리에 해당하는 뷰 포트에 표시되는 내용은 <p> 요소를 포함하지 않는다.

                        html - body - h1 - Hello,World!
        
        3. DOM은 개발도구에서 보이는 것은 아니다.

            - 개발도구의 요소 검사기는 DOM과 가장 가까운 근사치를 제공하지만, DOM에 없는 추가적인 정보를 포함한다.

            - 가장 좋은 예는 CSS의 가상 요소이다. ::before와 ::after 선택자를 사용하여 생성된 가상 요소는 CSSOM과 렌더트리의 일부를 구성한다.

            - 하지만, 기술적으로 DOM의 일부는 아니다. DOM은 오직 원본 HTML 문서로부터 빌드되고, 요소에 적용되는 스타일은 포함하지 않는다.

        4. 요약 
            - DOM은 HTML 문서에 대한 인터페이스입니다. 
            
                - 첫째로 뷰 포트에 무엇을 렌더링 할지 결정하기 위해 사용되며,
                
                - 둘째로는 페이지의 콘텐츠 및 구조, 그리고 스타일이 자바스크립트 프로그램에 의해 수정되기 위해 사용됩니다.

            - DOM은 원본 HTML 문서 형태와 비슷하지만 몇 가지 차이점이 있습니다.

                - 항상 유효한 HTML 형식입니다.
                
                - 자바스크립트에 수정될 수 있는 동적 모델이어야 합니다.
                
                - 가상 요소를 포함하지 않습니다. (Ex. ::after)
                
                - 보이지 않는 요소를 포함합니다. (Ex. display: none)

    - document object model
    
    - HTML 문서의 구조적 관계와 속성에 대한 모델
    
    - HTML 문서를 대표하는 트리구조 - 자식이 있고 부모가 있다.
    
    - JAVASCRIPT 에서 DOCUMENT 객체를 통해 전역으로 접근할 수 있다.
    
    - document 라고 대표되는 객체가 DOM 이다.
    
    - javascript 언어의 한 부분이 아니라, 자바스크립트를 이용해서 HTML을 이용할 수 있다.

    - 참고 : https://wit.nts-corp.com/2019/02/14/5522

* Node

    - DOM tree는 Node들로 구성되어있다.
    
        1. document node : 트리의 최상위 노드이다. element node와 text node에 접근하려면 document를 통해야 한다.
        
        2. element node : <div></div>, <span></span> 같은 태그를 말한다.
        
        3. text node : <span>안녕하세요</span> 에서 안녕하세요를 말한다.
        
        
2. HTML ELEMENT

    - element에서 원하는 TAG를 클릭하면 옆에 $0가 뜬다.
    
    - console 창에 console.dir($0) 치면, element안에 내장되어 있는 정보가 뜬다.
    
    - nodename : tag 네임
    
    - innerHTML : element 안에 있는 내용 
    
    - textContent : 내용 
    
    - style : css 
    
    - attribute : p tag 안에 있는 class, href 등등 전부
    
    - dataset
    
    - childeNodes / parentNode
    
    - children / parentElement
    
    - element
    
        1. 딱 element만 표현을 한다.
        
        2. element는 Node에 속해있다. 
        
    - node
    
        1. 공백(text)까지 포함시켜서 반영한다.
        
3. selecting element

    - 어떻게 HTML element를 자바스크립트를 이용해서 가져올 수 있는가?
    
        1. tag name을 이용 : getElementByTagName
        
        2. id 속성을 이용 : getElementById
        
        3. class name을 이용 : getElementByClassName
        
        4. selector를 이용 : querySelector / querySelectorAll
        
4. add event handler

    - event : 어떤 동작의 발생을 전달하기위해 객체가 보낸 메시지
    
        1. e.g : 웹페이지의 로드 / 버튼의 클릭 / resize / window가 open 되거나 load 등..
        
        2. DOM을 이용해 이벤트 핸들러를 추가할 수 있다.
        
                 A. onEventName(e.g.onClick)
                 
                    var elInput = document.getElementById("queryString");
                    
                    var elSearch = document.getElementById("search");
                    
                    elSearch.onClick = function(){
                    
                        alert(elInput.value);
                        
                    }
                    
                B. function createButton(){
                
                    var $btn = $('<button> Click me! </button>');
                    
                    var $body = $('body');
                    
                    btn.appendTo($body);
                    
                   }
                
                C. function createButton(){
                
                    $('<button>Click me!</button>').appendTo('body');
                    
                    }
                    
    - JQUERY 문법
    
        1. element 선택
            
            A. $(selector)
        
        2. element 생성
        
            A. $(htmlstring)
            
            B. $('<div></div>')
            
        3. 항상 JQUERY object를 리턴한다. (array like)
        
        4. USEFUL METHOD
        
            A. 조작
            
                - addClass / removeClass
                
                - html / text
                
                - append / appendTo ( 선택한 요소 내용의 끝에 콘텐트를 추가한다) 
                
                    A.append(B) : A에 B를 추가
                    A.appendTo(B) : B에 A를 추가
        
                - remove / empty
                
                - val : input, select, textarea 등의 form에서 값을 구한다 (value 값)
                
4. GUI / CLI

    - CLI (command line interface)
    
        1. 윈도우 커맨드 프롬프트에서 실행시킬 수 있는 그래픽 요소를 가지지 않는, 어플리케이션
        
    - GUI (graphical user interface)
    
        1. 일반적인 윈도우 어플리케이션처럼 창이뜨고 그 안에 뭔가 클릭하여 들어가는 식으로 그래픽 요소가 들어있는 어플

                
                
    
        
    
    
    
    