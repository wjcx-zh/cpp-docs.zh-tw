---
title: 編譯器警告 (層級 1) C4657
ms.date: 11/04/2016
f1_keywords:
- C4657
helpviewer_keywords:
- C4657
ms.assetid: eb750050-cea6-4ead-b80c-d5dcd4971cfc
ms.openlocfilehash: 92415d1d17c3342dbb721aa850f37f4dfabd1406
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62375687"
---
# <a name="compiler-warning-level-1-c4657"></a>編譯器警告 (層級 1) C4657

運算式包含自最新組建之後才新增的資料類型

您已加入或變更資料類型，使它成為對您的原始程式碼而言是上次成功組建之後所新增。 [編輯後繼續] 不支援對現有資料類型的變更。

這個警告後面一律會接著 [嚴重錯誤 C1092](../../error-messages/compiler-errors-1/fatal-error-c1092.md)。 如需詳細資訊，請參閱 [支援的程式碼變更](/visualstudio/debugger/supported-code-changes-cpp)。

### <a name="to-remove-this-warning-without-ending-the-current-debug-session"></a>移除這個警告，而不結束目前的偵錯工作階段

1. 請將資料類型改回錯誤之前的狀態。

1. 從 [偵錯]  功能表選擇 [套用程式碼變更] 。

### <a name="to-remove-this-error-without-changing-your-source-code"></a>移除這個錯誤，而不變更您的原始程式碼

1. 從 [偵錯]  功能表選擇 [停止偵錯] 。

1. 從 [建置]  功能表選擇 [建置] 。