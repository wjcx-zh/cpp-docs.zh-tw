---
title: 指示詞參考
ms.date: 07/15/2020
f1_keywords:
- Directives Reference
helpviewer_keywords:
- MASM (Microsoft Macro Assembler), directives reference
ms.assetid: da6efcd1-18f7-41de-81cd-a002a02f9a22
ms.openlocfilehash: 7ea9967bb3b617a798e7c573e93266faff5fb9a4
ms.sourcegitcommit: e15b46ea7888dbdd7e0bb47da76aeed680c3c1f3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/17/2020
ms.locfileid: "86446446"
---
# <a name="directives-reference"></a>指示詞參考

## <a name="x64"></a>x64

:::row:::
   :::column span="":::
      [`.ALLOCSTACK`](dot-allocstack.md)<br/>[`.ENDPROLOG`](dot-endprolog.md)<br/>[`PROC`](proc.md)
   :::column-end:::
   :::column span="":::
      [`.PUSHFRAME`](dot-pushframe.md)<br/>[`.PUSHREG`](dot-pushreg.md)<br/>[`.SAVEREG`](dot-savereg.md)
   :::column-end:::
   :::column span="":::
      [`.SAVEXMM128`](dot-savexmm128.md)<br/>[`.SETFRAME`](dot-setframe.md)
   :::column-end:::
:::row-end:::

## <a name="code-labels"></a>程式碼標籤

:::row:::
   :::column span="":::
      [`ALIGN`](align-masm.md)<br/>[`EVEN`](even.md)
   :::column-end:::
   :::column span="":::
      [`LABEL`](label-masm.md)
   :::column-end:::
   :::column span="":::
      [`ORG`](org.md)
   :::column-end:::
:::row-end:::

## <a name="conditional-assembly"></a>條件式元件

:::row:::
   :::column span="":::
      [`ELSE`](else-masm.md)<br/>[`ELSEIF`](elseif-masm.md)<br/>[`ELSEIF2`](elseif2.md)<br/>[`IF`](if-masm.md)<br/>[`IF2`](if2.md)
   :::column-end:::
   :::column span="":::
      [`IFB`](ifb.md)<br/>[`IFNB`](ifnb.md)<br/>[`IFDEF`](ifdef.md)<br/>[`IFNDEF`](ifndef.md)<br/>[`IFDIF`](ifdif.md)
   :::column-end:::
   :::column span="":::
      [`IFDIFI`](ifdif.md)<br/>[`IFE`](ife.md)<br/>[`IFIDN`](ifidn.md)<br/>[`IFIDNI`](ifidn.md)
   :::column-end:::
:::row-end:::

## <a name="conditional-control-flow"></a>條件式控制流程

:::row:::
   :::column span="":::
      [`.BREAK`](dot-break.md)<br/>[`.CONTINUE`](dot-continue.md)<br/>[`.ELSE`](dot-else.md)<br/>[`.ELSEIF`](dot-if.md)
   :::column-end:::
   :::column span="":::
      [`.ENDIF`](dot-endif.md)<br/>[`.ENDW`](dot-endw.md)<br/>[`.IF`](dot-if.md)<br/>[`.REPEAT`](dot-repeat.md)
   :::column-end:::
   :::column span="":::
      [`.UNTIL`](dot-until.md)<br/>[`.UNTILCXZ`](dot-untilcxz.md)<br/>[`.WHILE`](dot-while.md)
   :::column-end:::
:::row-end:::

## <a name="conditional-error"></a>條件式錯誤

:::row:::
   :::column span="":::
      [`.ERR`](dot-err.md)<br/>[`.ERR2`](dot-err2.md)<br/>[`.ERRB`](dot-errb.md)<br/>[`.ERRDEF`](dot-errdef.md)
   :::column-end:::
   :::column span="":::
      [`.ERRDIF`](dot-errdif.md)<br/>[`.ERRDIFI`](dot-errdif.md)<br/>[`.ERRE`](dot-erre.md)<br/>[`.ERRIDN`](dot-erridn.md)
   :::column-end:::
   :::column span="":::
      [`.ERRIDNI`](dot-erridn.md)<br/>[`.ERRNB`](dot-errnb.md)<br/>[`.ERRNDEF`](dot-errndef.md)<br/>[`.ERRNZ`](dot-errnz.md)
   :::column-end:::
:::row-end:::

## <a name="data-allocation"></a>資料配置

:::row:::
   :::column span="":::
      [`ALIGN`](align-masm.md)<br/>[`BYTE`](byte-masm.md)<br/>[`SBYTE`](sbyte-masm.md)<br/>[`DWORD`](dword.md)<br/>[`SDWORD`](sdword.md)<br/>[`EVEN`](even.md)
   :::column-end:::
   :::column span="":::
      [`FWORD`](fword.md)<br/>[`LABEL`](label-masm.md)<br/>[`ORG`](org.md)<br/>[`QWORD`](qword.md)<br/>[`REAL4`](real4.md)
   :::column-end:::
   :::column span="":::
      [`REAL8`](real8.md)<br/>[`REAL10`](real10.md)<br/>[`TBYTE`](tbyte.md)<br/>[`WORD`](word.md)<br/>[`SWORD`](sword.md)
   :::column-end:::
:::row-end:::

## <a name="equates"></a>等同于

:::row:::
   :::column span="":::
      [`=`](equal.md)
   :::column-end:::
   :::column span="":::
      [`EQU`](equ.md)
   :::column-end:::
   :::column span="":::
      [`TEXTEQU`](textequ.md)
   :::column-end:::
:::row-end:::

## <a name="listing-control"></a>清單控制項

:::row:::
   :::column span="":::
      [`.CREF`](dot-cref.md)<br/>[`.LIST`](dot-list.md)<br/>[`.LISTALL`](dot-listall.md)<br/>[`.LISTIF`](dot-listif.md)<br/>[`.LISTMACRO`](dot-listmacro.md)
   :::column-end:::
   :::column span="":::
      [`.LISTMACROALL`](dot-listmacroall.md)<br/>[`.NOCREF`](dot-nocref.md)<br/>[`.NOLIST`](dot-nolist.md)<br/>[`.NOLISTIF`](dot-nolistif.md)<br/>[`.NOLISTMACRO`](dot-nolistmacro.md)
   :::column-end:::
   :::column span="":::
      [`PAGE`](page.md)<br/>[`SUBTITLE`](subtitle.md)<br/>[`.TFCOND`](dot-tfcond.md)<br/>[`TITLE`](title.md)
   :::column-end:::
:::row-end:::

## <a name="macros"></a>巨集

:::row:::
   :::column span="":::
      [`ENDM`](endm.md)<br/>[`EXITM`](exitm.md)
   :::column-end:::
   :::column span="":::
      [`GOTO`](goto-masm.md)<br/>[`LOCAL`](local-masm.md)
   :::column-end:::
   :::column span="":::
      [`MACRO`](macro.md)<br/>[`PURGE`](purge.md)
   :::column-end:::
:::row-end:::

<br/><br/>

## <a name="miscellaneous"></a>其他

:::row:::
   :::column span="":::
      [`ALIAS`](alias-masm.md)<br/>[`ASSUME`](assume.md)<br/>[`COMMENT`](comment-masm.md)<br/>[`ECHO`](echo.md)<br/>[`END`](end-masm.md)<br/>[`.FPO`](dot-fpo.md)
   :::column-end:::
   :::column span="":::
      [`INCLUDE`](include-masm.md)<br/>[`INCLUDELIB`](includelib-masm.md)<br/>[`MMWORD`](mmword.md)<br/>[`OPTION`](option-masm.md)<br/>[`POPCONTEXT`](popcontext.md)
   :::column-end:::
   :::column span="":::
      [`PUSHCONTEXT`](pushcontext.md)<br/>[`.RADIX`](dot-radix.md)<br/>[`.SAFESEH`](dot-safeseh.md)<br/>[`XMMWORD`](xmmword.md)<br/>[`YMMWORD`](ymmword.md)
   :::column-end:::
:::row-end:::

## <a name="procedures"></a>程序

:::row:::
   :::column span="":::
      [`ENDP`](endp.md)<br/>[`INVOKE`](invoke.md)
   :::column-end:::
   :::column span="":::
      [`PROC`](proc.md)
   :::column-end:::
   :::column span="":::
      [`PROTO`](proto.md)
   :::column-end:::
:::row-end:::

## <a name="processor"></a>處理器

:::row:::
   :::column span="":::
      [`.386`](dot-386.md)<br/>[`.386P`](dot-386p.md)<br/>[`.387`](dot-387.md)<br/>[`.486`](dot-486.md)
   :::column-end:::
   :::column span="":::
      [`.486P`](dot-486p.md)<br/>[`.586`](dot-586.md)<br/>[`.586P`](dot-586p.md)<br/>[`.686`](dot-686.md)
   :::column-end:::
   :::column span="":::
      [`.686P`](dot-686p.md)<br/>[`.K3D`](dot-k3d.md)<br/>[`.MMX`](dot-mmx.md)<br/>[`.XMM`](dot-xmm.md)
   :::column-end:::
:::row-end:::

## <a name="repeat-blocks"></a>重複區塊

:::row:::
   :::column span="":::
      [`ENDM`](endm.md)<br/>[`FOR`](for-masm.md)
   :::column-end:::
   :::column span="":::
      [`FORC`](forc.md)<br/>[`GOTO`](goto-masm.md)
   :::column-end:::
   :::column span="":::
      [`REPEAT`](repeat.md)<br/>[`WHILE`](while-masm.md)
   :::column-end:::
:::row-end:::

## <a name="scope"></a>影響範圍

:::row:::
   :::column span="":::
      [`COMM`](comm.md)<br/>[`EXTERN`](extern-masm.md)
   :::column-end:::
   :::column span="":::
      [`EXTERNDEF`](externdef.md)<br/>[`INCLUDELIB`](includelib-masm.md)
   :::column-end:::
   :::column span="":::
      [`PUBLIC`](public-masm.md)
   :::column-end:::
:::row-end:::

## <a name="segment"></a>區段

:::row:::
   :::column span="":::
      [`.ALPHA`](dot-alpha.md)<br/>[`ASSUME`](assume.md)<br/>[`.DOSSEG`](dot-dosseg.md)
   :::column-end:::
   :::column span="":::
      [`END`](end-masm.md)<br/>[`ENDS`](ends-masm.md)<br/>[`GROUP`](group.md)
   :::column-end:::
   :::column span="":::
      [`SEGMENT`](segment.md)<br/>[`.SEQ`](dot-seq.md)
   :::column-end:::
:::row-end:::

## <a name="simplified-segment"></a>簡化區段

:::row:::
   :::column span="":::
      [`.CODE`](dot-code.md)<br/>[`.CONST`](dot-const.md)<br/>[`.DATA`](dot-data.md)<br/>[`.DATA?`](dot-data-q.md)
   :::column-end:::
   :::column span="":::
      [`.DOSSEG`](dot-dosseg.md)<br/>[`.EXIT`](dot-exit.md)<br/>[`.FARDATA`](dot-fardata.md)<br/>[`.FARDATA?`](dot-fardata-q.md)
   :::column-end:::
   :::column span="":::
      [`.MODEL`](dot-model.md)<br/>[`.STACK`](dot-stack.md)<br/>[`.STARTUP`](dot-startup.md)
   :::column-end:::
:::row-end:::

## <a name="string"></a>String

:::row:::
   :::column span="":::
      [`CATSTR`](catstr.md)<br/>[`INSTR`](instr.md)
   :::column-end:::
   :::column span="":::
      [`SIZESTR`](sizestr.md)
   :::column-end:::
   :::column span="":::
      [`SUBSTR`](substr.md)
   :::column-end:::
:::row-end:::

## <a name="structure-and-record"></a>結構和記錄

:::row:::
   :::column span="":::
      [`ENDS`](ends-masm.md)<br/>[`RECORD`](record-masm.md)
   :::column-end:::
   :::column span="":::
      [`STRUCT`](struct-masm.md)<br/>[`TYPEDEF`](typedef-masm.md)
   :::column-end:::
   :::column span="":::
      [`UNION`](union.md)
   :::column-end:::
:::row-end:::

## <a name="see-also"></a>請參閱

[Microsoft 巨集組譯參考](microsoft-macro-assembler-reference.md)\
[MASM BNF 文法](masm-bnf-grammar.md)
