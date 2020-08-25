---
title: 指示詞參考
ms.date: 07/15/2020
f1_keywords:
- Directives Reference
helpviewer_keywords:
- MASM (Microsoft Macro Assembler), directives reference
ms.assetid: da6efcd1-18f7-41de-81cd-a002a02f9a22
ms.openlocfilehash: e3e4fa7fbf18fbb18096593042873106897c70ca
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/25/2020
ms.locfileid: "88830744"
---
# <a name="directives-reference"></a>指示詞參考

## <a name="x64"></a>x64

:::row:::
   :::column span="":::
      [`.ALLOCSTACK`](dot-allocstack.md)\
      [`.ENDPROLOG`](dot-endprolog.md)\
      [`PROC`](proc.md)
   :::column-end:::
   :::column span="":::
      [`.PUSHFRAME`](dot-pushframe.md)\
      [`.PUSHREG`](dot-pushreg.md)\
      [`.SAVEREG`](dot-savereg.md)
   :::column-end:::
   :::column span="":::
      [`.SAVEXMM128`](dot-savexmm128.md)\
      [`.SETFRAME`](dot-setframe.md)
   :::column-end:::
:::row-end:::

## <a name="code-labels"></a>程式碼標籤

:::row:::
   :::column span="":::
      [`ALIGN`](align-masm.md)\
      [`EVEN`](even.md)
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
      [`ELSE`](else-masm.md)\
      [`ELSEIF`](elseif-masm.md)\
      [`ELSEIF2`](elseif2.md)\
      [`IF`](if-masm.md)\
      [`IF2`](if2.md)
   :::column-end:::
   :::column span="":::
      [`IFB`](ifb.md)\
      [`IFNB`](ifnb.md)\
      [`IFDEF`](ifdef.md)\
      [`IFNDEF`](ifndef.md)\
      [`IFDIF`](ifdif.md)
   :::column-end:::
   :::column span="":::
      [`IFDIFI`](ifdif.md)\
      [`IFE`](ife.md)\
      [`IFIDN`](ifidn.md)\
      [`IFIDNI`](ifidn.md)
   :::column-end:::
:::row-end:::

## <a name="conditional-control-flow"></a>條件式控制流程

:::row:::
   :::column span="":::
      [`.BREAK`](dot-break.md)\
      [`.CONTINUE`](dot-continue.md)\
      [`.ELSE`](dot-else.md)\
      [`.ELSEIF`](dot-if.md)
   :::column-end:::
   :::column span="":::
      [`.ENDIF`](dot-endif.md)\
      [`.ENDW`](dot-endw.md)\
      [`.IF`](dot-if.md)\
      [`.REPEAT`](dot-repeat.md)
   :::column-end:::
   :::column span="":::
      [`.UNTIL`](dot-until.md)\
      [`.UNTILCXZ`](dot-untilcxz.md)\
      [`.WHILE`](dot-while.md)
   :::column-end:::
:::row-end:::

## <a name="conditional-error"></a>條件式錯誤

:::row:::
   :::column span="":::
      [`.ERR`](dot-err.md)\
      [`.ERR2`](dot-err2.md)\
      [`.ERRB`](dot-errb.md)\
      [`.ERRDEF`](dot-errdef.md)
   :::column-end:::
   :::column span="":::
      [`.ERRDIF`](dot-errdif.md)\
      [`.ERRDIFI`](dot-errdif.md)\
      [`.ERRE`](dot-erre.md)\
      [`.ERRIDN`](dot-erridn.md)
   :::column-end:::
   :::column span="":::
      [`.ERRIDNI`](dot-erridn.md)\
      [`.ERRNB`](dot-errnb.md)\
      [`.ERRNDEF`](dot-errndef.md)\
      [`.ERRNZ`](dot-errnz.md)
   :::column-end:::
:::row-end:::

## <a name="data-allocation"></a>資料配置

:::row:::
   :::column span="":::
      [`ALIGN`](align-masm.md)\
      [`BYTE`](byte-masm.md)\
      [`SBYTE`](sbyte-masm.md)\
      [`DWORD`](dword.md)\
      [`SDWORD`](sdword.md)\
      [`EVEN`](even.md)
   :::column-end:::
   :::column span="":::
      [`FWORD`](fword.md)\
      [`LABEL`](label-masm.md)\
      [`ORG`](org.md)\
      [`QWORD`](qword.md)\
      [`REAL4`](real4.md)
   :::column-end:::
   :::column span="":::
      [`REAL8`](real8.md)\
      [`REAL10`](real10.md)\
      [`TBYTE`](tbyte.md)\
      [`WORD`](word.md)\
      [`SWORD`](sword.md)
   :::column-end:::
:::row-end:::

## <a name="equates"></a>等同

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
      [`.CREF`](dot-cref.md)\
      [`.LIST`](dot-list.md)\
      [`.LISTALL`](dot-listall.md)\
      [`.LISTIF`](dot-listif.md)\
      [`.LISTMACRO`](dot-listmacro.md)
   :::column-end:::
   :::column span="":::
      [`.LISTMACROALL`](dot-listmacroall.md)\
      [`.NOCREF`](dot-nocref.md)\
      [`.NOLIST`](dot-nolist.md)\
      [`.NOLISTIF`](dot-nolistif.md)\
      [`.NOLISTMACRO`](dot-nolistmacro.md)
   :::column-end:::
   :::column span="":::
      [`PAGE`](page.md)\
      [`SUBTITLE`](subtitle.md)\
      [`.TFCOND`](dot-tfcond.md)\
      [`TITLE`](title.md)
   :::column-end:::
:::row-end:::

## <a name="macros"></a>巨集

:::row:::
   :::column span="":::
      [`ENDM`](endm.md)\
      [`EXITM`](exitm.md)
   :::column-end:::
   :::column span="":::
      [`GOTO`](goto-masm.md)\
      [`LOCAL`](local-masm.md)
   :::column-end:::
   :::column span="":::
      [`MACRO`](macro.md)\
      [`PURGE`](purge.md)
   :::column-end:::
:::row-end:::

## <a name="miscellaneous"></a>其他

:::row:::
   :::column span="":::
      [`ALIAS`](alias-masm.md)\
      [`ASSUME`](assume.md)\
      [`COMMENT`](comment-masm.md)\
      [`ECHO`](echo.md)\
      [`END`](end-masm.md)\
      [`.FPO`](dot-fpo.md)
   :::column-end:::
   :::column span="":::
      [`INCLUDE`](include-masm.md)\
      [`INCLUDELIB`](includelib-masm.md)\
      [`MMWORD`](mmword.md)\
      [`OPTION`](option-masm.md)\
      [`POPCONTEXT`](popcontext.md)
   :::column-end:::
   :::column span="":::
      [`PUSHCONTEXT`](pushcontext.md)\
      [`.RADIX`](dot-radix.md)\
      [`.SAFESEH`](dot-safeseh.md)\
      [`XMMWORD`](xmmword.md)\
      [`YMMWORD`](ymmword.md)
   :::column-end:::
:::row-end:::

## <a name="procedures"></a>程序

:::row:::
   :::column span="":::
      [`ENDP`](endp.md)\
      [`INVOKE`](invoke.md)
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
      [`.386`](dot-386.md)\
      [`.386P`](dot-386p.md)\
      [`.387`](dot-387.md)\
      [`.486`](dot-486.md)
   :::column-end:::
   :::column span="":::
      [`.486P`](dot-486p.md)\
      [`.586`](dot-586.md)\
      [`.586P`](dot-586p.md)\
      [`.686`](dot-686.md)
   :::column-end:::
   :::column span="":::
      [`.686P`](dot-686p.md)\
      [`.K3D`](dot-k3d.md)\
      [`.MMX`](dot-mmx.md)\
      [`.XMM`](dot-xmm.md)
   :::column-end:::
:::row-end:::

## <a name="repeat-blocks"></a>重複區塊

:::row:::
   :::column span="":::
      [`ENDM`](endm.md)\
      [`FOR`](for-masm.md)
   :::column-end:::
   :::column span="":::
      [`FORC`](forc.md)\
      [`GOTO`](goto-masm.md)
   :::column-end:::
   :::column span="":::
      [`REPEAT`](repeat.md)\
      [`WHILE`](while-masm.md)
   :::column-end:::
:::row-end:::

## <a name="scope"></a>範圍

:::row:::
   :::column span="":::
      [`COMM`](comm.md)\
      [`EXTERN`](extern-masm.md)
   :::column-end:::
   :::column span="":::
      [`EXTERNDEF`](externdef.md)\
      [`INCLUDELIB`](includelib-masm.md)
   :::column-end:::
   :::column span="":::
      [`PUBLIC`](public-masm.md)
   :::column-end:::
:::row-end:::

## <a name="segment"></a>區段

:::row:::
   :::column span="":::
      [`.ALPHA`](dot-alpha.md)\
      [`ASSUME`](assume.md)\
      [`.DOSSEG`](dot-dosseg.md)
   :::column-end:::
   :::column span="":::
      [`END`](end-masm.md)\
      [`ENDS`](ends-masm.md)\
      [`GROUP`](group.md)
   :::column-end:::
   :::column span="":::
      [`SEGMENT`](segment.md)\
      [`.SEQ`](dot-seq.md)
   :::column-end:::
:::row-end:::

## <a name="simplified-segment"></a>簡化區段

:::row:::
   :::column span="":::
      [`.CODE`](dot-code.md)\
      [`.CONST`](dot-const.md)\
      [`.DATA`](dot-data.md)\
      [`.DATA?`](dot-data-q.md)
   :::column-end:::
   :::column span="":::
      [`.DOSSEG`](dot-dosseg.md)\
      [`.EXIT`](dot-exit.md)\
      [`.FARDATA`](dot-fardata.md)\
      [`.FARDATA?`](dot-fardata-q.md)
   :::column-end:::
   :::column span="":::
      [`.MODEL`](dot-model.md)\
      [`.STACK`](dot-stack.md)\
      [`.STARTUP`](dot-startup.md)
   :::column-end:::
:::row-end:::

## <a name="string"></a>字串

:::row:::
   :::column span="":::
      [`CATSTR`](catstr.md)\
      [`INSTR`](instr.md)
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
      [`ENDS`](ends-masm.md)\
      [`RECORD`](record-masm.md)
   :::column-end:::
   :::column span="":::
      [`STRUCT`](struct-masm.md)\
      [`TYPEDEF`](typedef-masm.md)
   :::column-end:::
   :::column span="":::
      [`UNION`](union.md)
   :::column-end:::
:::row-end:::

## <a name="see-also"></a>另請參閱

[Microsoft 巨集群組合器參考](microsoft-macro-assembler-reference.md)\
[MASM BNF 文法](masm-bnf-grammar.md)
