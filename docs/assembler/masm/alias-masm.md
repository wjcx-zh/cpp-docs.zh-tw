---
title: ALIAS (MASM)
ms.date: 08/30/2018
f1_keywords:
- Alias
helpviewer_keywords:
- ALIAS directive
ms.assetid: d9725c49-58de-41da-ab01-b06a56cf5cf2
ms.openlocfilehash: ab00092f410d34119e876db4562e6d0709743d79
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62166486"
---
# <a name="alias-masm"></a>ALIAS (MASM)

**別名**指示詞會建立函式的替代名稱。  這可讓您建立函式的多個名稱，或建立可讓連結器 (LINK.exe) 將舊的函式對應至新的函式的程式庫。

## <a name="syntax"></a>語法

> 別名\<*別名*> = \<*實際名稱*>

#### <a name="parameters"></a>參數

*actual-name*<br/>
函式或程序的實際名稱。  角括號是必要的。

*alias*<br/>
其他名稱或別名名稱。  角括號是必要的。

## <a name="see-also"></a>另請參閱

[指示詞參考](../../assembler/masm/directives-reference.md)<br/>