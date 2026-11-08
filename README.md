# Project Information: 프로젝트 소개, 선택 이유, 원본 GitHub URL 및 라이선스
이 프로젝트는 오늘 할 일을 정리하는 todo list 수정 프로그램이다. 체크를 누르면 오늘 한 일을 완성된 상태로 둘 수 있고, 체크 되지 않은 일은 active인 상태가 된다. 또한 삭제 버튼을 누르면 삭제되는 기능도 구현했다. 

- 선택 이유 : 
가장 간단하면서도, java script를 배울때 다루었던 crud의 기본 구성이 모두 들어있고, react로 CRUD 서비스는 어떻게 구현되는지 궁금해서 이 프로젝트를 선택했다. 그리고 

- 원본 github URL : 
https://github.com/mdn/todo-react.git
- 라이센스 : 
github의 LICENCE파일에 상세히 기록.

# Installation: 설치·실행 방법 및 실행 화면
설치 방법은 
1. 터미널에 git clone으로 파일을 불러온다.
git clone https://github.com/mdn/todo-react.git
2. cd <파일 이름> 을 통해서 현재 clone으로 만들어진 파일로 이동한다. 
3. npm install로 현재 필요한 필수 패키지를 설치해준다. 
4. npm run dev 명령어로 프로그램을 실행한다. 
-  실행화면
![alt text](image.png)

# Source Code Exploration: 주요 파일, 컴포넌트, 코드 분석
- 주요 파일 
1. App.jsx
할일 목록을 관리하고, 추가 및 삭제 기능을 하위 컴포넌트들을 배치하여서 구현하였다.
2. Todo.jsx
목록에 표시되는 각 항목들을 이 파일에서 관리한다. 완료를 나타내는 체크박스나 입력된 텍스트 내용, 수정 및 삭제 버튼 구성이 이 파일에서 관리된다.
3. Form.jsx
오늘 할일을 입력받고 add 버튼을 누르면 텍스트 내용이 전달된다. 이렇게 전달된 데이터는 App.jsx로 가서 해당 내용의 id를 부여받고, completed:false를 받는다. check 버튼으로 이를 변경할 수 있다.
- 컴포넌트
1. FilterButton : 해당 id의 체크박스의 체크 여부를 확인하고 체크되어있는 경우, 체크되지 않은 경우, 전체 경우로 나뉘어져서, 각 해당 버튼을 클릭하면 App.jsx의 필터 상태를 업데이트하고 각 상황에 맞게 화면에 뜨도록 설정한다.
2. Todo 컴포넌트 : 목록의 하나의 요소를 다루는 컴포넌트이다. 특히, edit버튼을 누르면 입력한 할일을 수정할 수 있는데 이 컴포넌트를 통해서 현재 edit버튼을 눌러서 수정하는 상황인지 아니면 그냥 리스트에 떠있기만 한 상황인지에 따라 다른 처리를 해준다. 
- 코드 분석
  const taskList = tasks
    ?.filter(FILTER_MAP[filter])
    .map((task) => (
      <Todo
        id={task.id}
        name={task.name}
        completed={task.completed}
        key={task.id}
        toggleTaskCompleted={toggleTaskCompleted}
        deleteTask={deleteTask}
        editTask={editTask}
      />
    ));
    우선, 이 코드는 조건에 따른 할일 리스트를 화면에 띄우는 코드이다. 여기서 filter()를 사용하여, 현재 그 할일 목록이 all인 상황인지, active인 상황인지, completed인 상황인지에 따라 조건에 맞지 않는 목록은 다 걸러낸다.
    또한 map()을 사용해서, 배열의 개수만큼 반복하여 데이터값을 인덱스로 받아와서 Todo 컴포넌트로 변환해주는 역할을 한다. id={task.id}처럼 데이터를 jsx문법을 활용하여 key값에 변경된 데이터를 전달해준다. 또한, deleteTask={deleteTask}, editTask={editTask} 처럼, 삭제버튼이나 수정 버튼을 누르면 해당 함수를 호출해주는 역할을 한다.

# Customizing: 수정한 3가지 내용, 수정 파일명 및 전/후 결과
1. text 수정: componets폴더에 있는 Form.jsx에서 어떤 내용을 입력받을지 구하는 질문을 수정했다. 
what needs to be done? 이라는 질문에서 오늘 당신이 해야하는 일은 무엇인가요?로 변경함.
2. 색상 수정 : index.css에서 .btn.toggle-btn[aria-pressed="true"] 부분에 background 색을 남색으로 설정하여 선택된 항목이 남색이 되어 알아보기 쉽도록 설정했다. 또한 delete버튼의 border색을 노란색으로 설정하여 더욱 눈에 잘 띄도록 설정했다.
3. validation 추가 : 아무 것도 입력하지 않고 add버튼을 눌렀을때, 할 일을 입력하세요 라고 alert()해주는 기능을 추가하였다. (원래는 없었음.)
# Deployment: 실제 접근 가능한 Vercel URL

# Weekly Review:
- 새롭게 배운 내용 3가지
1. JSX 문법 중에서 event 속성을 다룰때는 camel case로 첫번째단어는 소문자 시작 두번째 단어 부터 구분용으로 대문자 사용한다. 
2. inline으로 style을 넣을 때는 style ={{}}와 같이 중괄호를 두번 겹쳐서 사용한다.
3. react rendering은 index.html -> main.jsx -> App.jsx -> BOM순으로 데이터와 변경된 값들이 넘어가면서 web브라우저 화면에 렌더링 된다.
- 어려웠던 점과 해결 방법
먼저, Form.jsx에서는 자바 스크립트 역할을 하고, form control의역할을 하며, 화면에 그려지는건 App.jsx가 html역할을 한다는 것이 어려웠다. 그러나 각종 요소들을 수정해보고 삭제해가면서 계속 화면에 렌더링 해가면서 어떤 부분인지 파악했다. 
- AI 활용 내용 및 느낀 점
프로그램에서 form의 validation을 추가하고 싶었는데 어떤 함수를 다루어야 하는지 잘 파악하지 못했다. 그러나 AI를 통해서 Form.jsx에서 handlerSubmit함수에 그 기능을 추가하면 된다는 것을 알 수 있었다.