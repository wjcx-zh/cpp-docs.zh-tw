---
title: 編譯器警告 （層級 1） C4656 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4656
dev_langs:
- C++
helpviewer_keywords:
- C4656
ms.assetid: b5aaef74-2320-4345-a6ae-b813881a491c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 3334b9448dd6e9d47ed0b3ee3e4dfb9dfc57b57f
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46032404"
---
# <a name="compiler-warning-level-1-c4656"></a>編譯器警告 (層級 1) C4656

'symbol': 資料類型的新或自上次組建中，已變更或其他處有不同定義

您已加入或變更資料類型，使它成為對您的原始程式碼而言是上次成功組建之後所新增。 [編輯後繼續] 不支援對現有資料類型的變更。

這個警告後面一律會接著 [嚴重錯誤 C1092](../../error-messages/compiler-errors-1/fatal-error-c1092.md)。 如需詳細資訊，請參閱 [支援的程式碼變更](/visualstudio/debugger/supported-code-changes-cpp)。

### <a name="to-remove-this-warning-without-ending-the-current-debug-session"></a>移除這個警告，而不結束目前的偵錯工作階段

1. 請將資料類型改回錯誤之前的狀態。

1. 從 [偵錯]  功能表選擇 [套用程式碼變更] 。

### <a name="to-remove-this-error-without-changing-your-source-code"></a>移除這個錯誤，而不變更您的原始程式碼

1. 從 [偵錯]  功能表選擇 [停止偵錯] 。

1. 從 [建置]  功能表選擇 [建置] 。