---
title: OPTION (MASM)
ms.date: 08/30/2018
f1_keywords:
- option
helpviewer_keywords:
- OPTION directive
ms.assetid: 8e10dabd-e36f-4586-ab01-ada96736b0bd
ms.openlocfilehash: a8215bf1f816baa490a768fb2cab0b3c2e53e20b
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62217253"
---
# <a name="option-masm"></a>OPTION (MASM)

啟用和停用 「 組合器 」 的功能。

## <a name="syntax"></a>語法

> 選項*optionlist*

## <a name="remarks"></a>備註

可用的選項包括：

|||||
|-|-|-|-|
|**CASEMAP**|**DOTNAME**|**NODOTNAME**|**模擬器**|
|**NOEMULATOR**|**結尾**|**EXPR16**|**EXPR32**|
|**語言**|**LJMP**|**NOLJMP**|**M510**|
|**NOM510**|**NOKEYWORD**|**NOSIGNEXTEND**|**OFFSET**|
|**OLDMACROS**|**NOOLDMACROS**|**OLDSTRUCTS**|**NOOLDSTRUCTS**|
|**PROC**|**序言**|**READONLY**|**NOREADONLY**|
|**範圍**|**NOSCOPED**|**SEGMENT**|**SETIF2**。|

語言的語法是**選項的語言：**<em>x</em>，其中*x*是 C，SYSCALL、 STDCALL、 PASCAL、 FORTRAN、 或 BASIC 的其中一個。  SYSCALL、 PASCAL、 FORTRAN、 BASIC 不支援與搭配[。模型](../../assembler/masm/dot-model.md)一般。

## <a name="see-also"></a>另請參閱

[指示詞參考](../../assembler/masm/directives-reference.md)<br/>