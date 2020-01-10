---
title: MACRO
ms.date: 12/16/2019
f1_keywords:
- MACRO
helpviewer_keywords:
- MACRO directive
ms.assetid: 89434f7c-bc2c-4e91-8940-fe2db8785233
ms.openlocfilehash: 23c6b0aefae856da449da574669e8475122c7556
ms.sourcegitcommit: 0781c69b22797c41630601a176b9ea541be4f2a3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/20/2019
ms.locfileid: "75312946"
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

## <a name="see-also"></a>請參閱

指示詞[參考](directives-reference.md)\
[GOTO （MASM）](goto-masm.md)\
[ENDM](endm.md)\
[MASM BNF 文法](masm-bnf-grammar.md)

