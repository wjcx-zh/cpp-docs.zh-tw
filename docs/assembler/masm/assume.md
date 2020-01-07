---
title: ASSUME
ms.date: 11/05/2019
f1_keywords:
- ASSUME
helpviewer_keywords:
- ASSUME directive
ms.assetid: cd162070-aee9-4c65-babc-005c6cc73d7c
ms.openlocfilehash: a74a5336e626f561f1fc61e866792ce193332d84
ms.sourcegitcommit: 0781c69b22797c41630601a176b9ea541be4f2a3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/20/2019
ms.locfileid: "75316534"
---
# <a name="assume"></a>ASSUME

啟用註冊值的錯誤檢查。 （僅限 32-bit MASM）。

## <a name="syntax"></a>語法

> **假設**  *segregister* __：__ *name* ⟦ __，__ *segregister* __：__ *name*.。。⟧\
> **假設**  *dataregister* __：__ *type* ⟦ __，__ *dataregister* __：__ *type*.。。⟧\
> **假設**  *register* __： error__ ⟦ __，__ *register* __： error__.。。⟧\
> **假設**⟦*register* __：__ ⟧**無**⟦ __，__ *register* __：沒有__.。。⟧

## <a name="remarks"></a>備註

在**假設**生效後，組合器會監看給定暫存器值的變更。 如果使用了暫存器，**錯誤**就會產生錯誤。 **任何內容都**不會移除註冊錯誤檢查。 您可以在一個語句中結合不同類型的假設。

## <a name="see-also"></a>請參閱

指示詞[參考](directives-reference.md)\
[MASM BNF 文法](masm-bnf-grammar.md)
