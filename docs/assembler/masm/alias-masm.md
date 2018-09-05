---
title: ALIAS (MASM) |Microsoft Docs
ms.custom: ''
ms.date: 08/30/2018
ms.technology:
- cpp-masm
ms.topic: reference
f1_keywords:
- Alias
dev_langs:
- C++
helpviewer_keywords:
- ALIAS directive
ms.assetid: d9725c49-58de-41da-ab01-b06a56cf5cf2
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c6a977d35040d8ca25cd3bd4ae4def233092b37a
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2018
ms.locfileid: "43691058"
---
# <a name="alias-masm"></a>ALIAS (MASM)

**別名**指示詞會建立函式的替代名稱。  這可讓您建立函式的多個名稱，或建立可讓連結器 (LINK.exe) 將舊的函式對應至新的函式的程式庫。

## <a name="syntax"></a>語法

> 別名\<*別名*> = \<*實際名稱*>

#### <a name="parameters"></a>參數

*實際名稱*<br/>
函式或程序的實際名稱。  角括號是必要的。

*alias*<br/>
其他名稱或別名名稱。  角括號是必要的。

## <a name="see-also"></a>另請參閱

[指示詞參考](../../assembler/masm/directives-reference.md)<br/>