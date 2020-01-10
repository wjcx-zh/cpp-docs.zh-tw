---
title: MASM 運算子參考
ms.date: 12/17/2019
helpviewer_keywords:
- MASM (Microsoft Macro Assembler), operators reference
- operators [MASM]
ms.assetid: c069cab7-d6b0-4f82-a6ce-0ca3fc7e6428
ms.openlocfilehash: c0059ab1b0204b79e040d18bd5aa88145775ebcd
ms.sourcegitcommit: 0781c69b22797c41630601a176b9ea541be4f2a3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/20/2019
ms.locfileid: "75318757"
---
# <a name="masm-operators-reference"></a>MASM 運算子參考

## <a name="arithmetic"></a>算術

||||
|-|-|-|
|[* （乘）](operator-multiply.md)|[+ （新增）](operator-add.md)|[-（減或否定）](operator-subtract-2.md)|
|[.欄位](operator-dot.md)|[/（除）](operator-subtract-1.md)|[&#91;&#93;指數](operator-brackets.md)|
|[MOD （餘數）](operator-mod.md)|||

## <a name="control-flow"></a>控制流程

||||
|-|-|-|
|[\! （執行時間邏輯 not）](operator-logical-not-masm-run-time.md)|[\!= （執行時間不等於）](operator-not-equal-masm.md)|[&#124;&#124;（執行時間邏輯 or）](operator-logical-or.md)|
|[& & （執行時間邏輯 and）](operator-logical-and-masm-run-time.md)|[< （執行時間小於）](operator-less-than-masm-run-time.md)|[\<= （執行時間小於或等於）](operator-less-or-equal-masm-run-time.md)|
|[= = （執行時間相等）](operator-equal-masm-run-time.md)|[> （執行時間大於）](operator-greater-than-masm-run-time.md)|[> = （執行時間大於或等於）](operator-greater-or-equal-masm-run-time.md)|
|[& （執行時間位 and）](operator-bitwise-and.md)|||
|[傳遞?（執行時間執行測試）](operator-carry-q.md)|[溢出?（執行時間溢位測試）](operator-overflow-q.md)|[校驗?（執行時間同位檢查測試）](operator-parity-q.md)|
|[簽訂?（執行時間簽署測試）](operator-sign-q.md)|[零?（執行時間零測試）](operator-zero-q.md)||

## <a name="logical-and-shift"></a>邏輯 and Shift

||||
|-|-|-|
|[AND （位 and）](operator-and.md)|[NOT （位 not）](operator-not.md)|[OR （位 or）](operator-or.md)|
|[SHL （向左移位位）](operator-shl.md)|[SHR （shift 位 right）](operator-shr.md)|[XOR （位互斥 or）](operator-xor.md)|

## <a name="macro"></a>巨集

||||
|-|-|-|
|[\! （字元常值）](operator-logical-not-masm.md)|[% （視為文字）](operator-percent.md)||
|[;;（視為批註）](operator-semicolons.md)|[&lt; &gt; （視為一個常值）](operator-literal.md)|[& & （替代參數值）](operator-logical-and-masm.md)|

## <a name="miscellaneous"></a>其他

||||
|-|-|-|
|[' ' （視為字串）](operator-single-quote.md)|["" （視為字串）](operator-double-quote.md)||
|：（本機標籤定義）|：：（註冊區段和位移）|：：（全域標籤定義）|
|[;（視為批註）](operator-semicolon.md)|[DUP （重複宣告）](operator-dup.md)||

## <a name="record"></a>資料錄

|||
|-|-|
|[MASK （取得記錄或欄位位元遮罩）](operator-mask.md)|[寬度（取得記錄或欄位寬度）](operator-width.md)|

## <a name="relational"></a>關聯性

||||
|-|-|-|
|[EQ （等於）](operator-eq.md)|[GE （大於或等於）](operator-ge.md)|[GT （大於）](operator-gt.md)|
|[LE （小於或等於）](operator-le.md)|[LT （小於）](operator-lt.md)|[NE （不等於）](operator-ne.md)|

## <a name="segment"></a>區隔

|||
|-|-|
|[：（區段覆寫）](operator-colon.md)|：：（註冊區段和位移）|
|[IMAGEREL （影像相對位移）](operator-imagerel.md)|[LROFFSET （載入器已解決的位移）](operator-lroffset.md)|
|[OFFSET （線段相對位移）](operator-offset.md)|[SECTIONREL （區段相對位移）](operator-sectionrel.md)|
|[SEG （取得區段）](operator-seg.md)||

## <a name="type"></a>類型

||||
|-|-|-|
|[高（高8位，最低16位）](operator-high.md)|[HIGH32 （高32位64位）](operator-high32.md)|[HIGHWORD （高16位，最低32位）](operator-highword.md)|
|[長度（陣列中的元素數目）](operator-length.md)|[LENGTHOF （陣列中的元素數目）](operator-lengthof.md)|[低（低8位）](operator-low.md)|
|[LOW32 （低32位）](operator-low32.md)|[LOWWORD （低16位）](operator-lowword.md)|[OPATTR （取得引數類型資訊）](operator-opattr.md)|
|[PTR （或類型的指標）](operator-ptr.md)|[SHORT （標記簡短標籤類型）](operator-short.md)|[大小（類型或變數的大小）](operator-size.md)|
|[SIZEOF （類型或變數的大小）](operator-sizeof.md)|[這個（目前的位置）](operator-this.md)|[類型（取得運算式類型）](operator-type.md)|
|[.類型（取得引數類型資訊）](operator-dot-type.md)|||

## <a name="see-also"></a>請參閱

[Microsoft 巨集組譯參考](microsoft-macro-assembler-reference.md)\
[MASM BNF 文法](masm-bnf-grammar.md)
