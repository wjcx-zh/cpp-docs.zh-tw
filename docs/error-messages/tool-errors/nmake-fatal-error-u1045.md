---
title: NMAKE 嚴重錯誤 U1045
ms.date: 08/11/2019
f1_keywords:
- U1045
helpviewer_keywords:
- U1045
ms.assetid: dc70d162-14b9-4107-9237-7514044d72e3
ms.openlocfilehash: bdc28bcf02aea791a346a0a74915707fef551b8b
ms.sourcegitcommit: db1ed91fa7451ade91c3fb76bc7a2b857f8a5eef
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/13/2019
ms.locfileid: "68980537"
---
# <a name="nmake-fatal-error-u1045"></a>NMAKE 嚴重錯誤 U1045

> 衍生失敗:*訊息*

NMAKE 所呼叫的程式或命令因*message*中的原因而失敗。 當 NMAKE 呼叫另一個程式 (例如編譯器或連結器) 時, 呼叫可能會失敗。 或者, 被呼叫的程式可能會傳回錯誤。 此訊息用來報告錯誤。

如果要修正這個問題，請先判斷錯誤的原因。 您可以使用 NMAKE [/n](../../build/reference/running-nmake.md#nmake-options)選項所報告的命令來確認環境設定, 並在命令列上重複 NMAKE 所完成的動作。
