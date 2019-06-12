# Learning memo

memo for myself

<hr>
## functino

### Random

#### Math.floor(Math.random() \* length)

Math.floor: 小数点を切り下げて、整数を返す。
Math.random: 0~1 の間でランダムに小数点を返す。 最大値は 0.9 \* #8(Array) で 7 を返す。
ただ、このやり方だとどうしても Index が小さいものがあたりやすい。

let randIdx = Math.floor(Math.random() \* hand2.length);

<hr>

#### Arrow function for (p) => (do what)

この例は (p)=>{do what}と違うやり方。
例: slice(-3)でうしろから 3 桁を切り取っている。4 桁の場合、前の 0 は一つ無くなる。
範囲は number が 999 以下の場合。 => の後は ( ) で括っている。

let padToThree = (number) => (number <= 999 ? `00${number}`.slice(-3) : number);

<hr>
## Method

### slice

選択範囲を切り取る。

<hr>
### .splice
選択範囲を切り取って、Arrayを変更し、切り取ったものを返す。
ARRAY.splice(start, QTY); リストで返す。 [0]を付けると、1番目を返す。

<hr>
### .reduce
ARRAY.reduce((previous, current)=> previous + current.value, default value);
previousに変数を宣言し、そこに値が溜まっていく

例:
let hand1 = [];
let hand2 = [...this.props.pokemon];
while (hand1.length < hand2.length) {
let randIdx = Math.floor(Math.random() \* hand2.length);
let randPokemon = hand2.splice(randIdx, 1)[0];
hand1.push(randPokemon);
}
let exp1 = hand1.reduce((exp, pokemon) => exp + pokemon.base_experience, 0);
let exp2 = hand2.reduce((exp, pokemon) => exp + pokemon.base_experience, 0);

<hr>
## Operator
### if ? yes : no

{this.props.isWinner ? "Winner" : "Loser!"}
→ これを別のコードで書く。

let title;
if (this.props.isWinner) {
title = <h1 className="Pokedex-winner">Winning Hand</h1>;
} else {
title = <h1 className="Pokedex-loser">Losing Hand</h1>;

→ JSX で
{title}

<hr>
### propsでBoonleanか、TrueかFalseを渡す。
比較結果でTrueかFalseを渡せる。
例
<Pokedex pokemon={hand1} exp={exp1} isWinner={exp1 > exp2} />
