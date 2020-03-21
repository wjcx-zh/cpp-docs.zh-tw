---
title: MACRO
ms.date: 12/16/2019
f1_keywords:
- MACRO
helpviewer_keywords:
- MACRO directive
ms.assetid: 89434f7c-bc2c-4e91-8940-fe2db8785233
ms.openlocfilehash: 8eb0afdf73270c3e741f43b2e1fba02fe965846c
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/21/2020
ms.locfileid: "80076141"
---
# <a name="macro"></a>MACRO

標記名為*name*的宏區塊，並為呼叫宏時所傳遞的引數建立*參數*預留位置。

## <a name="syntax"></a>語法

> *name***宏**⟦*parameter* ⟦ **：需求**|： =*default* | *args* **： VARARG**⟧ .。。⟧\
> *語句*\
⟦**GOTO** ：*macrolabelId*⟧ \
> ⟦**EXITM**⟧ \
> **ENDM** ⟦*value*⟧

## <a name="remarks"></a>備註

宏函式會將*值*傳回給呼叫語句。

## <a name="see-also"></a>另請參閱

指示詞[參考](directives-reference.md)\
[GOTO （MASM）](goto-masm.md)\
[ENDM](endm.md)\
[MASM BNF 文法](masm-bnf-grammar.md)
