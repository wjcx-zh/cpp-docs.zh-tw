---
title: Naked 函式呼叫
ms.date: 11/04/2016
helpviewer_keywords:
- virtual device drivers
- VXD virtual device drivers
- virtual device drivers, naked function calls
- naked functions
- prolog code
- epilog code
- naked keyword [C++]
- naked keyword [C++], storage-class attribute
ms.assetid: 2a66847a-a43f-4541-a7be-c9f5f29b5fdb
ms.openlocfilehash: 9b49d34d7276d3c9260488f23d1821b9708d2481
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87227318"
---
# <a name="naked-function-calls"></a>Naked 函式呼叫

**Microsoft 特定的**

以屬性宣告的函式會在沒有初構或終解程式 **`naked`** 代碼的情況下發出，讓您使用[內嵌](../assembler/inline/inline-assembler.md)組合語言撰寫自己的自訂初構/終解序列。 Naked 函式是做為進階功能提供。 這些函式可讓您宣告從 C/C++ 以外的內容呼叫的函式，因此對於參數位置以及要保留哪些暫存器會做出不同的假設。 範例包括像是中斷處理常式這類常式。 這項功能對於虛擬裝置驅動程式 (VxD) 的撰寫者特別實用。

## <a name="what-do-you-want-to-know-more-about"></a>您還想知道關於哪些方面的詳細資訊？

- [naked](../cpp/naked-cpp.md)

- [Naked 函式的規則和限制](../cpp/rules-and-limitations-for-naked-functions.md)

- [撰寫初構/終解程式碼的考慮](../cpp/considerations-for-writing-prolog-epilog-code.md)

**結束 Microsoft 專有**

## <a name="see-also"></a>另請參閱

[呼叫慣例](../cpp/calling-conventions.md)
