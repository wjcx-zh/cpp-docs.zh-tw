---
title: 編譯器警告 (層級 1) C4655
ms.date: 08/27/2018
f1_keywords:
- C4655
helpviewer_keywords:
- C4655
ms.assetid: 540f2c7a-e4a1-49af-84b4-03eeea1bbf41
ms.openlocfilehash: d4c409c2d69099853a872142e05ef0fcda5a7655
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80199527"
---
# <a name="compiler-warning-level-1-c4655"></a>編譯器警告 (層級 1) C4655

> '*symbol*'：自上次組建之後，變數類型是新的，或在其他地方有不同的定義

## <a name="remarks"></a>備註

自從上次成功組建後，您已變更或加入新的資料類型。 [編輯後繼續] 不支援對現有資料類型的變更。

這個警告後面接著 [嚴重錯誤 C1092](../../error-messages/compiler-errors-1/fatal-error-c1092.md)。 如需詳細資訊，請參閱 [支援的程式碼變更](/visualstudio/debugger/supported-code-changes-cpp)。

### <a name="to-remove-this-warning-without-ending-the-current-debug-session"></a>移除這個警告，而不結束目前的偵錯工作階段

1. 請將資料類型改回錯誤之前的狀態。

2. 從 [偵錯] 功能表選擇 [套用程式碼變更]。

### <a name="to-remove-this-warning-without-changing-your-source-code"></a>移除這個警告，而不變更您的程式碼

1. 從 [偵錯] 功能表選擇 [停止偵錯]。

2. 從 [建置] 功能表選擇 [建置]。
