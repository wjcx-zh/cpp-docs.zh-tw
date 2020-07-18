---
title: MASM 運算子參考
ms.date: 07/15/2020
helpviewer_keywords:
- MASM (Microsoft Macro Assembler), operators reference
- operators [MASM]
ms.assetid: c069cab7-d6b0-4f82-a6ce-0ca3fc7e6428
ms.openlocfilehash: c29b173a1dcf29c297e41f136044599fbd5218a5
ms.sourcegitcommit: e15b46ea7888dbdd7e0bb47da76aeed680c3c1f3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/17/2020
ms.locfileid: "86446459"
---
# <a name="masm-operators-reference"></a>MASM 運算子參考

## <a name="arithmetic"></a>算術

:::row:::
   :::column span="":::
      [`*`乘以](operator-multiply.md)<br/>[`+`載入](operator-add.md)<br/>[`-`（減或否定）](operator-subtract-2.md)
   :::column-end:::
   :::column span="":::
      [`.`欄位](operator-dot.md)<br/>[`/`拆分](operator-subtract-1.md)
   :::column-end:::
   :::column span="":::
      [`[]`指數](operator-brackets.md)<br/>[`MOD`數量](operator-mod.md)
   :::column-end:::
:::row-end:::

## <a name="control-flow"></a>控制流程

:::row:::
   :::column span="":::
      [`!`（執行時間邏輯 not）](operator-logical-not-masm-run-time.md)<br/>[`!=`（執行時間不等於）](operator-not-equal-masm.md)<br/>[`||`（執行時間邏輯 or）](operator-logical-or.md)<br/>[`&&`（執行時間邏輯 and）](operator-logical-and-masm-run-time.md)<br/>[`<`（執行時間小於）](operator-less-than-masm-run-time.md)
   :::column-end:::
   :::column span="":::
      [`<=`（執行時間小於或等於）](operator-less-or-equal-masm-run-time.md)<br/>[`==`（執行時間相等）](operator-equal-masm-run-time.md)<br/>[`>`（執行時間大於）](operator-greater-than-masm-run-time.md)<br/>[`>=`（執行時間大於或等於）](operator-greater-or-equal-masm-run-time.md)<br/>[`&`（執行時間位 and）](operator-bitwise-and.md)
   :::column-end:::
   :::column span="":::
      [`CARRY?`（執行時間執行測試）](operator-carry-q.md)<br/>[`OVERFLOW?`（執行時間溢位測試）](operator-overflow-q.md)<br/>[`PARITY?`（執行時間同位檢查測試）](operator-parity-q.md)<br/>[`SIGN?`（執行時間簽署測試）](operator-sign-q.md)<br/>[`ZERO?`（執行時間零測試）](operator-zero-q.md)
   :::column-end:::
:::row-end:::

## <a name="logical-and-shift"></a>邏輯 and Shift

:::row:::
   :::column span="":::
      [`AND`（位 and）](operator-and.md)<br/>[`NOT`（位 not）](operator-not.md)
   :::column-end:::
   :::column span="":::
      [`OR`（位 or）](operator-or.md)<br/>[`SHL`（向左移位位）](operator-shl.md)
   :::column-end:::
   :::column span="":::
      [`SHR`（右移位 right）](operator-shr.md)<br/>[`XOR`（位互斥 or）](operator-xor.md)
   :::column-end:::
:::row-end:::

## <a name="macro"></a>巨集

:::row:::
   :::column span="":::
      [`!`（字元常值）](operator-logical-not-masm.md)<br/>[`%`（視為文字）](operator-percent.md)
   :::column-end:::
   :::column span="":::
      [`;;`（視為批註）](operator-semicolons.md)<br/>[`< >`（視為一個常值）](operator-literal.md)
   :::column-end:::
   :::column span="":::
      [`& &`（替代參數值）](operator-logical-and-masm.md)
   :::column-end:::
:::row-end:::

## <a name="miscellaneous"></a>其他

:::row:::
   :::column span="":::
      [`' '`（視為字串）](operator-single-quote.md)<br/>[`" "`（視為字串）](operator-double-quote.md)<br/>`:`（本機標籤定義）
   :::column-end:::
   :::column span="":::
      `::`（註冊區段和位移）<br/>`::`（全域標籤定義）
   :::column-end:::
   :::column span="":::
      [`;`（視為批註）](operator-semicolon.md)<br/>[`DUP`（重複宣告）](operator-dup.md)
   :::column-end:::
:::row-end:::

## <a name="record"></a>記錄

:::row:::
   :::column span="":::
      [`MASK`（取得記錄或欄位位元遮罩）](operator-mask.md)
   :::column-end:::
   :::column span="2":::
      [`WIDTH`（取得記錄或欄位寬度）](operator-width.md)
   :::column-end:::
:::row-end:::

## <a name="relational"></a>關聯式

:::row:::
   :::column span="":::
      [`EQ`等於](operator-eq.md)<br/>[`GE`（大於或等於）](operator-ge.md)
   :::column-end:::
   :::column span="":::
      [`GT`（大於）](operator-gt.md)<br/>[`LE`（小於或等於）](operator-le.md)
   :::column-end:::
   :::column span="":::
      [`LT`（小於）](operator-lt.md)<br/>[`NE`（不等於）](operator-ne.md)
   :::column-end:::
:::row-end:::

## <a name="segment"></a>區段

:::row:::
   :::column span="":::
      [`:`（區段覆寫）](operator-colon.md)<br/>`::`（註冊區段和位移）<br/>[`IMAGEREL`（影像相對位移）](operator-imagerel.md)
   :::column-end:::
   :::column span="":::
      [`LROFFSET`（載入器已解決的位移）](operator-lroffset.md)<br/>[`OFFSET`（區段相對位移）](operator-offset.md)
   :::column-end:::
   :::column span="":::
      [`SECTIONREL`（區段相對位移）](operator-sectionrel.md)<br/>[`SEG`（取得區段）](operator-seg.md)
   :::column-end:::
:::row-end:::

## <a name="type"></a>類型

:::row:::
   :::column span="":::
      [`HIGH`（高8位，最低16位）](operator-high.md)<br/>[`HIGH32`（高32位的64位）](operator-high32.md)<br/>[`HIGHWORD`（最低32位的高16位）](operator-highword.md)<br/>[`LENGTH`（陣列中的元素數目）](operator-length.md)<br/>[`LENGTHOF`（陣列中的元素數目）](operator-lengthof.md)<br/>[`LOW`（低8位）](operator-low.md)
   :::column-end:::
   :::column span="":::
      [`LOW32`（低32位）](operator-low32.md)<br/>[`LOWWORD`（低16位）](operator-lowword.md)<br/>[`OPATTR`（取得引數類型資訊）](operator-opattr.md)<br/>[`PTR`（或類型的指標）](operator-ptr.md)<br/>[`SHORT`（標記簡短標籤類型）](operator-short.md)
   :::column-end:::
   :::column span="":::
      [`SIZE`（類型或變數的大小）](operator-size.md)<br/>[`SIZEOF`（類型或變數的大小）](operator-sizeof.md)<br/>[`THIS`（目前的位置）](operator-this.md)<br/>[`TYPE`（取得運算式類型）](operator-type.md)<br/>[`.TYPE`（取得引數類型資訊）](operator-dot-type.md)
   :::column-end:::
:::row-end:::

## <a name="see-also"></a>請參閱

[Microsoft 巨集組譯參考](microsoft-macro-assembler-reference.md)\
[MASM BNF 文法](masm-bnf-grammar.md)
