# TIL

## Today I Learned.

- React
    - 2021.08.16
        - Class로 Props 받을 때 : {this.props.propName}
        - Function으로 Props 받을 때 : 함수 파라미터로 props전달 → {props.propName}

            ![스크린샷 2021-08-16 오후 6.14.56.png](TIL%203ec87a85bd3a401d9b7ad5ddcdd954b8/%E1%84%89%E1%85%B3%E1%84%8F%E1%85%B3%E1%84%85%E1%85%B5%E1%86%AB%E1%84%89%E1%85%A3%E1%86%BA_2021-08-16_%E1%84%8B%E1%85%A9%E1%84%92%E1%85%AE_6.14.56.png)

            ![스크린샷 2021-08-16 오후 6.12.43.png](TIL%203ec87a85bd3a401d9b7ad5ddcdd954b8/%E1%84%89%E1%85%B3%E1%84%8F%E1%85%B3%E1%84%85%E1%85%B5%E1%86%AB%E1%84%89%E1%85%A3%E1%86%BA_2021-08-16_%E1%84%8B%E1%85%A9%E1%84%92%E1%85%AE_6.12.43.png)

            ---

        - **Hook**

            → Function으로 Class의 기능을 최대한 사용하기 위해

            → 이름이 use로 시작

            1. Function에서 **state** 사용하는 방법. (Class에서는 내부 함수 bind(this)때문에 불편..)
                - **useState** → 2개의 값으로 이루어진 배열이 리턴됨

                    : 첫번째 값(0번째 인덱스)이 원하는 State값

                    ![스크린샷 2021-08-16 오후 6.26.21.png](TIL%203ec87a85bd3a401d9b7ad5ddcdd954b8/%E1%84%89%E1%85%B3%E1%84%8F%E1%85%B3%E1%84%85%E1%85%B5%E1%86%AB%E1%84%89%E1%85%A3%E1%86%BA_2021-08-16_%E1%84%8B%E1%85%A9%E1%84%92%E1%85%AE_6.26.21.png)

                    : 두번째 값이 state를 변경하기 위한 **함수** 

                    → 인자에 변경하기로 원하는 값 전달 ex) setNumber(Math.random())

                    ![스크린샷 2021-08-16 오후 6.31.25.png](TIL%203ec87a85bd3a401d9b7ad5ddcdd954b8/%E1%84%89%E1%85%B3%E1%84%8F%E1%85%B3%E1%84%85%E1%85%B5%E1%86%AB%E1%84%89%E1%85%A3%E1%86%BA_2021-08-16_%E1%84%8B%E1%85%A9%E1%84%92%E1%85%AE_6.31.25.png)

                    : 아래와 같이 많이 사용

                    → _date에는 state값, setDate에는 state를 변경하기 위한 함수

                    ![스크린샷 2021-08-16 오후 6.35.28.png](TIL%203ec87a85bd3a401d9b7ad5ddcdd954b8/%E1%84%89%E1%85%B3%E1%84%8F%E1%85%B3%E1%84%85%E1%85%B5%E1%86%AB%E1%84%89%E1%85%A3%E1%86%BA_2021-08-16_%E1%84%8B%E1%85%A9%E1%84%92%E1%85%AE_6.35.28.png)

            1. Function에서 **라이프 사이클**(Life Cycle) 활용하는 방법.
                - Class에서 라이프 사이클 사용하는 방법
                    - 라이프 사이클(Life Cycle) 흐름도

                        ![스크린샷 2021-08-16 오후 10.37.49.png](TIL%203ec87a85bd3a401d9b7ad5ddcdd954b8/%E1%84%89%E1%85%B3%E1%84%8F%E1%85%B3%E1%84%85%E1%85%B5%E1%86%AB%E1%84%89%E1%85%A3%E1%86%BA_2021-08-16_%E1%84%8B%E1%85%A9%E1%84%92%E1%85%AE_10.37.49.png)

                    - 예제코드

                        ```jsx
                        componentWillMount(){
                        	console.log("componentWillMount");
                        }

                        componentDidMount(){
                        	console.log("componentDidMount");
                        }

                        render(){
                        	return() {
                        				{/* code */}
                        	}
                        }
                        ```

                        위와 같이 사용하면 

                        componentWillMount() → render() → componentDidMount() 순서로 동작

                        ```jsx
                        shouldComponentUpdate(nextProps, nextState){
                        	{/* code */}
                        }

                        componentWillUpdate(nextProps, nextState){
                        	{/* code */}
                        }

                        render(){
                        	{/* code */}
                        }

                        componentDidUpdate(nextProps, nextState){
                        	{/* code */}
                        }
                        ```

                        component가 생성된 다음에 render()가 호출 되기 전 

                        shouldComponentUpdate를 통해 render()가 호출할 필요가 있는지 없는지 판단

                        → true를 리턴하면 render() 호출, false를 리턴하면 호출 안함

                        → 클래스 방식에서는 라이플 사이클에 따라서 정해진 이름의 메소드를 호출함으로써 원하는 타이밍에 원하는 코드를 호출 가능

                - 함수가 실행된 후에 추가적으로 필요한 작업 수행하도록 하는 방법

                    → **useEffect** 사용

                    ```jsx
                    useEffect(function(){
                    	{/* code */}
                    });
                    ```

                    위와 같이 사용하면 render()가 끝난 다음 useEffect 함수의 인자로 전달된 함수가 동작

                    → 클래스의 **ComponentDidMount** & **ComponentDidUpdate**와 같은 효과

                    ```jsx
                    useEffect(function(){
                    	{/* code */}
                    },[]);
                    ```

                    함수의 2번째 인자로 **빈배열**을 전달하면 컴포넌트가 최초로 생성될 때 딱 한 번만 실행돼서**componentDidMount()**와 같은 효과

                - Component가 소멸될 때 청산 작업 (Cleanup)

                    → **useEffect에 return값**으로 함수 전달

                    ```jsx
                    useEffect(function(){
                    	{/* code1 */}
                    	
                    	return function(){
                    		{/* code2 */}
                    	}
                    });
                    ```

                    위와 같이 사용하면 useEffect (code1)함수가 실행된 후 다시 실행 되는 경우, 다시 실행되기 직전에 code2가 실행됨 == 다시 실행되기 전 이전 작업을 정리

                    → 클래스의 **ComponentWillUnmount()**와 같은 효과

                - 성능 향상을 위해 불필요한 작업 생략 (변화한 값에 대한 처리만 실행하도록)

                    → **useEffect 마지막 인자에 배열 추가**

                    ```jsx
                    var numberState = useState(props.initNumber);
                    var number = numberState[0];

                    useEffect(function(){
                    	{/* code1 */}
                    	document.title = number;
                    }, [number]);
                    ```

                    위와 같이 사용하면 마지막 인자인 배열의 원소가 변경되었을 때만 code1 함수가 호출됨

        - Hook 사용 예제 코드

            ![스크린샷 2021-08-16 오후 11.45.23.png](TIL%203ec87a85bd3a401d9b7ad5ddcdd954b8/%E1%84%89%E1%85%B3%E1%84%8F%E1%85%B3%E1%84%85%E1%85%B5%E1%86%AB%E1%84%89%E1%85%A3%E1%86%BA_2021-08-16_%E1%84%8B%E1%85%A9%E1%84%92%E1%85%AE_11.45.23.png)

            → 각 버튼 클릭하면 funcShow, classShow 값이 true에서 false로 바뀌면서 Component 사라짐
