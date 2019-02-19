---
title: 預設訊號
ms.date: 11/04/2016
helpviewer_keywords:
- default signals
- defaults, signals
ms.assetid: db9fc17b-75c0-4d33-86be-c536584bbede
ms.openlocfilehash: bb84e168d0693313373395e8d5f44be0eca9891e
ms.sourcegitcommit: f4be868c0d1d78e550fba105d4d3c993743a1f4b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/12/2019
ms.locfileid: "56152556"
---
# <a name="default-signals"></a>預設訊號

**ANSI 4.7.1.1** 如果沒有在呼叫訊號處理常式之前執行 `signal(sig, SIG_DFL)` 的同等項，會封鎖所執行的訊號

在程式開始執行時，訊號會設定為其預設狀態。

## <a name="see-also"></a>另請參閱

[程式庫函式](../c-language/library-functions.md)
