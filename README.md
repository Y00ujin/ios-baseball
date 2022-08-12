## BaseBall Game
#### 컴퓨터가 제공하는 세자리수의 각 숫자와 위치를 맞추는 게임을 Xcode Command Line Tool로 구현했다.

<br>
<br>

## Index
- ### 기능, 설계 및 구현, trouble shooting, 학습한 내용, FlowChart

<br>
<br>

## 기능
### 1. 메뉴 선택 기능
#### 게임을 시작하거나, 누군가 승리하여 게임이 끝났을 때 메뉴를 선택할 수 있다. 메뉴 선택에는 두 가지 선택지가 있으며, 게임 시작과 게임 종료의 선택지가 있다. 1을 선택할 시 야구 게임이 시작되고 2를 선택할 시 프로그램이 종료된다.

<p align="center">
<img width="523" alt="스크린샷 2022-08-12 오후 7 38 08" src="https://user-images.githubusercontent.com/71479613/184337877-82e80abe-3359-417b-81c5-6e048fb9c284.png">
</p>




<br>

### 2. 야구 게임 기능
#### 야구 게임을 진행할 수 있다. 사용자는 띄어쓰기로 분리된 세 개의 수를 입력할 수 있으며, 숫자 입력 후에는 스트라이크와 볼의 개수와 남은 횟수를 확인할 수 있다. 주어진 횟수 내에 정답을 맞출 시 사용자가 승리한다. 주어진 횟수 내에 정답을 맞추지 못할 시 컴퓨터가 승리한다.
<p align="center">
<img width="523" alt="스크린샷 2022-08-12 오후 7 41 26" src="https://user-images.githubusercontent.com/71479613/184338360-2b35b362-c50d-4d8b-b6ea-6a82c5de659a.png">
</p>

<br>
<br>

## 설계 및 구현
- ### 1. `getSelectMenuAnswer()` : 메뉴를 출력한 후 사용자의 입력을 받아 반환한다.
<br>

- ### 2. `startBaseBallGame()` : `getSelectMenuAnswer()` 함수를 호출하여 반환되는 사용자의 입력을 통해 게임을 시작하거나 프로그램을 종료시킨다. 
<br>

- ### 3. `createComputerNumbers()` : 세자리수의 정답을 생성하여 반환하는 함수
#### 3-1. random함수를 사용하여 1부터 9 사이의 랜덤 수를 생성한다.
#### 3-2.생성된 수를  [Int] 타입의 randomNumbers의 count가 3이 될 때까지 삽입한다.
<br>

- ### 4. `ischeckedUserNumbers()` : 사용자가 입력한 규칙에 맞체 입력하였는지 판단하는 함수
#### 4-1. 사용자의 입력이 공백이거나, 띄어쓰기로 3개의 숫자를 구분하여 입력하지 않았다면 false를 반환한다.
#### 4-2. 입력한 각 숫자가 1부터 9 사이의 숫자가 아니면 false를 반환한다.
#### 4-3. 입력한 각 숫자가 1부터 9 사이의 숫자라면 trur를 반환한다.
<br>


- ### 5. `ischeckedExistWinner()` : 스트라이크와 볼 개수, 남은 기회를 확인하여 승리자가 있는지 판별하는 함수
#### 5-1. compareComputerNumbers() 함수에서 반환된 스트라이크 개수가 3개라면 사용자 승리를 출력합니다.
#### 5-2. 남은 기회가 0이라면 컴퓨터 승리를 출력한다.
#### 5-3. 컴퓨터나 사용자가 승리했을 시에는 true를 반환하고 승리하지 않았을 때에는 false를 반환한다.
<br>

- ### 6. `startPlayGame()` : `createComputerNumbers()` 함수를 호출하여 정답을 생성한 후 사용자의 입력을 받아 `ischeckedUserNumbers()` 함수를 호출하여 사용자의 입력이 유효한지 판단하고 사용자가 입력한 숫자와 정답이 같은지 `ischeckedExistWinner()` 함수를 호출하여 판단합니다.
<br>

- ### 7. `compareComputerNumbers()` : 사용자가 입력한 숫자와 정답을 비교하여 스트라이크와 볼의 개수를 구해 반환합니다.
#### 7-1. [Int] 타입인 computerNumbers와 [Int] 타입인 userNumbers의 각 index에 접근하여 숫자가 같은지 체크한다. 같은 Count를 기록하여 strikeCount 변수에 담아 반환한다.
#### 7-2. computerNumbers와 userNumbers를 Set으로 형변환하여 교집합 연산을 한 Count를 구한다. 이 Count는 strikeCount도 포함되어있는 값이므로 strikeCount를 빼준 뒤 ballCount에 담아 반환한다.

<br>
<br>

## 학습 내용
### 1. Set
#### 중복된 값을 포함하지 않으며 교집합, 차집합, 합집합 등 집합 연산이 가능하다.

<br>

### 2. Naming
#### Bool 값을 반환하는 함수는 is 접두사를 사용하며 복수 타입을 다루는 변수, 상수는 복수형으로 네이밍한다.
<br>

### 3. Code Convention
#### 여는 중괄호는 항상 한칸 띄워 작성한다.
```Swift
if ...(여기 한칸 띄우기){

}

for ...(여기 한칸 띄우기){

}

func ...(여기 한칸 띄우기){

}
```
<br>
<br>

## BaseBall Game FlowChart
<p align="center">
<img width="378" alt="스크린샷 2022-08-11 오전 9 26 48" src="https://user-images.githubusercontent.com/71479613/184045242-f4fa1f7a-4426-43fb-b21b-bbc5f92e3843.png">
</p>
