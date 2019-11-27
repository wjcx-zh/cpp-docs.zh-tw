---
title: OPTION (MASM)
ms.date: 08/30/2018
f1_keywords:
- option
helpviewer_keywords:
- OPTION directive
ms.assetid: 8e10dabd-e36f-4586-ab01-ada96736b0bd
ms.openlocfilehash: 0f90ab0115c3dde894d468bbbe60ffa0193b8336
ms.sourcegitcommit: 9ee5df398bfd30a42739632de3e165874cb675c3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74395173"
---
# <a name="option-masm"></a>OPTION (MASM)

啟用和停用組合器的功能。

## <a name="syntax"></a>語法

> **選項** *optionlist*

## <a name="remarks"></a>備註

可用的選項包括：

|||||
|-|-|-|-|
|**CASEMAP**|**DOTNAME**|**NODOTNAME**|**模擬器**|
|**NOEMULATOR**|**結尾**|**EXPR16**|**EXPR32**|
|**語言**|**LJMP**|**NOLJMP**|**M510**|
|**NOM510**|**NOKEYWORD**|**NOSIGNEXTEND**|**投影**|
|**OLDMACROS**|**NOOLDMACROS**|**OLDSTRUCTS**|**NOOLDSTRUCTS**|
|**PROC**|**說明**|**唯讀**|**NOREADONLY**|
|**範圍**|**NOSCOPED**|**SEGMENT**|**SETIF2**。|

LANGUAGE 的語法是**OPTION language：** <em>x</em>，其中*x*是 C、SYSCALL、STDCALL、PASCAL、FORTRAN 或 BASIC 其中之一。  與搭配使用時，不支援 SYSCALL、PASCAL、FORTRAN 和 BASIC [。模型](../../assembler/masm/dot-model.md)平面。

## <a name="see-also"></a>另請參閱

[指示詞參考](directives-reference.md)
