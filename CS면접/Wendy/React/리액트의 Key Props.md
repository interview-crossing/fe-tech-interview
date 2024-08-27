# 리액트에서의 Key Prop

-   각 컴포넌트가 어떤 배열 항목에 해당하는지 리액트가 식별함.
-   Key값을 통해 변화를 추론하고 DOM트리를 업데이트 한다.
-   단일 컴포넌트에서는 Prop와 state로 변화를 추론하고 업데이트하기때문에 Key값으로 관리할 필요가 없다.
-   리액트에서 Key prop 은 주로 리스트나 동적 자식 요소가있는 경우에 사용된다.

## Key 를 index 값으로 활용할 때의 문제점

-   key 사용중 배열이 재배열되거나 중간에 데이터값이 추가되었을경우 key값 또한 바뀌게된다
-   변경된 부분만 캐치하여 랜더시키는것이 아니라 전체가 변경되었다고 판단하여 전체 리렌더가 일어난다.

//예시

```tsx
const Children = () => {
    const [items, setItems] = useState([
        { id: 6, name: "wendy" },
        { id: 1, name: "riel" },
        { id: 2, name: "chan" },
        { id: 3, name: "gang" },
        { id: 4, name: "jeff" },
        { id: 5, name: "amy" },
    ]);

    const shuffleItems = () => {
        const shuffled = [...items].reverse(); // 순서 반전
        setItems(shuffled);
    };

    return (
        <div style={{ textAlign: "center" }}>
            <h2>Index as key:</h2>
            <div
                style={{
                    display: "flex",
                    flexDirection: "column",
                    alignItems: "center",
                }}
            >
                {items.map((item, index) => (
                    <div
                        key={index}
                        style={{
                            padding: "10px",
                            border: "1px solid black",
                            marginBottom: "5px",
                        }}
                    >
                        {item.id} / {item.name} / key : {index}
                    </div>
                ))}
            </div>

            <h2>ID as key:</h2>
            <div
                style={{
                    display: "flex",
                    flexDirection: "column",
                    alignItems: "center",
                }}
            >
                {items.map((item) => (
                    <div
                        key={item.id}
                        style={{
                            padding: "10px",
                            border: "1px solid black",
                            marginBottom: "5px",
                        }}
                    >
                        {item.id} / {item.name} / key : {item.id}
                    </div>
                ))}
            </div>

            <button onClick={shuffleItems} style={{ marginTop: "20px" }}>
                순서 바꾸기
            </button>
        </div>
    );
};
export default Children;
```
