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
ms.openlocfilehash: f9d8a8747d4a808d040b814005782ed8187bf274
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50528267"
---
# <a name="naked-function-calls"></a>Naked 函式呼叫

## <a name="microsoft-specific"></a>Microsoft 特定的

以宣告的函式**naked**屬性會發出沒有初構和終解程式碼，讓您撰寫使用您自己自訂的初構/終解序列[內嵌組譯工具](../assembler/inline/inline-assembler.md)。 Naked 函式是做為進階功能提供。 這些函式可讓您宣告從 C/C++ 以外的內容呼叫的函式，因此對於參數位置以及要保留哪些暫存器會做出不同的假設。 範例包括像是中斷處理常式這類常式。 這項功能對於虛擬裝置驅動程式 (VxD) 的撰寫者特別實用。

## <a name="what-do-you-want-to-know-more-about"></a>您還想知道關於哪些方面的詳細資訊？

- [naked](../cpp/naked-cpp.md)

- [Naked 函式的規則和限制](../cpp/rules-and-limitations-for-naked-functions.md)

- [撰寫初構/終解程式碼的考量](../cpp/considerations-for-writing-prolog-epilog-code.md)

**結束 Microsoft 專屬**

## <a name="see-also"></a>另請參閱

[呼叫慣例](../cpp/calling-conventions.md)