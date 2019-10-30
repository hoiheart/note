# 개요 및 기본 타입

### 타입스크립트

정적 타입 시스템\(static type system\)을 도입한 자바스크립트의 상위 집합  
프로그램의 예상 동작을 타입을 통해 나타내고, 그 예상에 걸맞게 동작할 지의 여부를 타입 검사기를 통해 실행 전에 확인할 수 있다.

### 기본 타입

#### 불리언

```typescript
const isType: boolean = true;
```

#### 숫자

```typescript
const point: number = 100;
```

#### 문자

```typescript
const message: string = 'hello';
```

#### null

```typescript
const nullValue: null = null;
```

#### undefined

```typescript
const undefinedValue: undefined = undefined;
```

#### any \(비권장\)

```typescript
let bool: any = true;
```

#### void

```typescript
function nothing(): void { }
```

#### never

```typescript
function alwaysThrow(): never {
  throw new Error(`I'm a wicked function!`);
}
```

#### 배열

```typescript
const num: number[] = [0, 1, 2];
const str: string[] = ['str1', 'str2', 'str3'];
```

#### 튜플

원소의 수와 각 원소의 타입이 정확히 지정된 배열의 타입을 정의

```typescript
const arr: [string, number] = ['123', 123];
```

#### 객체

```typescript
const user: { name: string; id: number; } = { name: 'John', id: 1234 };
```

#### 선택 속성

```typescript
const user: { name: string; id?: number; } = { name: 'John' };
```

#### 읽기 전용 속성

```typescript
const user: { name: string; readonly id: number; } = { name: 'John', id: 1234 };
```



