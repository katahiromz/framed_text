# framed_text

## 概要

JavaScriptで枠付きテキストを書きます。

<img src="img/screenshot.png" alt="[スクリーンショット]" />

## コード

```js
// 枠付きテキストを描画する
const drawFramedText = (ctx, text, x, y, fontSize, data, fillStyle = "black", fontName = "sans-serif", align = "left", baseline = "top") => {
    ctx.font = `${fontSize}px ${fontName}`;
    ctx.textAlign = align;
    ctx.textBaseline = baseline;
    ctx.lineJoin = "round"; // 枠の角を丸くして綺麗にする

    for (let item of data) {
        ctx.lineWidth = item.thickness * 2;
        ctx.strokeStyle = item.color;
        
        const dx = item.dx || 0;
        const dy = item.dy || 0;
        ctx.strokeText(text, x + dx, y + dy);
    }
    
    ctx.fillStyle = fillStyle;
    ctx.fillText(text, x, y);
};

// 使い方
drawFramedText(ctx, "枠付きテキスト", 10, 10, 35, [
    { color: "gray", thickness: 10, dx: 5, dy: 5 },
    { color: "yellow", thickness: 10 },
    { color: "white", thickness: 8 },
    { color: "blue", thickness: 2 },
], "red");
drawFramedText(ctx, "やっほー", 60, 60, 55, [
    { color: "gray", thickness: 6, dx: 2, dy: 2 },
    { color: "red", thickness: 4 },
], "white");
```
