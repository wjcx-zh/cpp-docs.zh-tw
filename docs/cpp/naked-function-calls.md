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
ms.openlocfilehash: 242fe83807c6608a09492d0f1f817e3b6e50e530
ms.sourcegitcommit: a6d63c07ab9ec251c48bc003ab2933cf01263f19
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2019
ms.locfileid: "74857394"
---
# <a name="naked-function-calls"></a>Naked 函式呼叫

**Microsoft 專屬**

以**naked**屬性宣告的函式會在沒有初構或終解程式碼的情況下發出，讓您使用[內嵌](../assembler/inline/inline-assembler.md)組合語言撰寫自己的自訂初構/終解序列。 Naked 函式是做為進階功能提供。 這些函式可讓您宣告從 C/C++ 以外的內容呼叫的函式，因此對於參數位置以及要保留哪些暫存器會做出不同的假設。 範例包括像是中斷處理常式這類常式。 這項功能對於虛擬裝置驅動程式 (VxD) 的撰寫者特別實用。

## <a name="what-do-you-want-to-know-more-about"></a>您還想知道關於哪些方面的詳細資訊？

- [naked](../cpp/naked-cpp.md)

- [Naked 函式的規則和限制](../cpp/rules-and-limitations-for-naked-functions.md)

- [撰寫初構/終解程式碼的考量](../cpp/considerations-for-writing-prolog-epilog-code.md)

**結束 Microsoft 專屬**

## <a name="see-also"></a>請參閱

[呼叫慣例](../cpp/calling-conventions.md)