---
title: MASM 運算子參考
ms.date: 08/30/2018
helpviewer_keywords:
- MASM (Microsoft Macro Assembler), operators reference
- operators [MASM]
ms.assetid: c069cab7-d6b0-4f82-a6ce-0ca3fc7e6428
ms.openlocfilehash: cb97c5dcb640b8d8592d842afd7dbb8cf9d0852c
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50430455"
---
# <a name="masm-operators-reference"></a>MASM 運算子參考

## <a name="arithmetic"></a>算術運算

||||
|-|-|-|
|[* （乘）](operator-multiply.md)|[+ （加號）](operator-add.md)|[-（減法或否定）](operator-subtract-2.md)|
|[.（欄位）](operator-dot.md)|[/ （除法）](operator-subtract-1.md)|[&#91;&#93;（索引）](operator-brackets.md)|
|[MOD （餘數）](operator-mod.md)|||

## <a name="control-flow"></a>控制流程

||||
|-|-|-|
|[\! (執行階段邏輯 not)](operator-logical-not-masm-run-time.md)|[\!= （不等於執行階段）](operator-not-equal-masm.md)|[&#124;&#124;(邏輯的執行階段或)](operator-logical-or.md)|
|[& & (邏輯的執行階段和)](operator-logical-and-masm-run-time.md)|[< (執行階段小於)](operator-less-than-masm-run-time.md)|[\<= （小於或等於執行階段）](operator-less-or-equal-masm-run-time.md)|
|[= = （等於執行階段）](operator-equal-masm-run-time.md)|[> （大於執行階段）](operator-greater-than-masm-run-time.md)|[> = （大於或等於執行階段）](operator-greater-or-equal-masm-run-time.md)|
|[& (位元執行階段和)](operator-bitwise-and.md)|||
|[CARRY？（執行階段所包含的測試）](operator-carry-q.md)|[OVERFLOW？（執行階段發生溢位測試）](operator-overflow-q.md)|[同位嗎？（執行階段同位檢查測試）](operator-parity-q.md)|
|[登入嗎？（執行階段的符號檢驗）](operator-sign-q.md)|[零嗎？（執行階段零測試）](operator-zero-q.md)||

## <a name="logical-and-shift"></a>邏輯和 shift 鍵

||||
|-|-|-|
|[和 (位元和)](operator-and.md)|[不 (位元 not)](operator-not.md)|[OR (位元或)](operator-or.md)|
|[SHL （shift 位元向左）](operator-shl.md)|[SHR （右移位位元）](operator-shr.md)|[XOR (位元互斥或)](operator-xor.md)|

## <a name="macro"></a>巨集

||||
|-|-|-|
|[\! （字元常值）](operator-logical-not-masm.md)|[%（視為文字）](operator-percent.md)||
|[;;（視為註解）](operator-semicolons.md)|[&lt; &gt; （將視為一個常值）](operator-literal.md)|[& & （取代參數值）](operator-logical-and-masm.md)|

## <a name="miscellaneous"></a>其他

||||
|-|-|-|
|['' （視為字串）](operator-single-quote.md)|[""（視為字串）](operator-double-quote.md)||
|: （本機標籤定義)|:: （註冊區段和位移)|:: （全域標籤定義)|
|[;（視為註解）](operator-semicolon.md)|[DUP （重複宣告）](operator-dup.md)||

## <a name="record"></a>資料錄

|||
|-|-|
|[遮罩 （取得記錄或欄位的位元遮罩）](operator-mask.md)|[寬度 （取得記錄或欄位的寬度）](operator-width.md)|

## <a name="relational"></a>關聯性

||||
|-|-|-|
|[EQ （等於）](operator-eq.md)|[GE （大於或等於）](operator-ge.md)|[GT （大於）](operator-gt.md)|
|[LE （小於或等於）](operator-le.md)|[LT （小於）](operator-lt.md)|[NE （不等於）](operator-ne.md)|

## <a name="segment"></a>區段

|||
|-|-|
|[: （區段覆寫)](operator-colon.md)|:: （註冊區段和位移)|
|[IMAGEREL （映像的相對位移）](operator-imagerel.md)|[LROFFSET （載入器會解析位移）](operator-lroffset.md)|
|[位移 （區段的相對位移）](operator-offset.md)|[SECTIONREL （區段的相對位移）](operator-sectionrel.md)|
|[SEG （get 區段）](operator-seg.md)||

## <a name="type"></a>類型

||||
|-|-|-|
|[高 （高 8 位元的最低的 16 位元）](operator-high.md)|[HIGH32 （高 32 位元的 64 位元）](operator-high32.md)|[HIGHWORD （高 16 位元最低的 32 位元）](operator-highword.md)|
|[長度 （數字陣列中的項目）](operator-length.md)|[LENGTHOF （數字陣列中的項目）](operator-lengthof.md)|[LOW （低 8 位元）](operator-low.md)|
|[LOW32 （低 32 位元）](operator-low32.md)|[LOWWORD （低 16 位元）](operator-lowword.md)|[OPATTR （取得引數類型資訊）](operator-opattr.md)|
|[PTR （指標或做為類型）](operator-ptr.md)|[SHORT （mark 簡短標籤型別）](operator-short.md)|[大小 （類型或變數的大小）](operator-size.md)|
|[SIZEOF （類型或變數的大小）](operator-sizeof.md)|[這個 （目前的位置）](operator-this.md)|[型別 （get 運算式型別）](operator-type.md)|
|[.型別 （取得引數類型資訊）](operator-dot-type.md)|||

## <a name="see-also"></a>另請參閱

[Microsoft 巨集組譯工具參考](microsoft-macro-assembler-reference.md)<br/>
