---
title: 其他啟動考量
ms.date: 11/04/2016
helpviewer_keywords:
- program startup [C++]
- startup code
- initializing before main
ms.assetid: 0e942aa6-8342-447c-b068-8980ed7622bd
ms.openlocfilehash: 16e48f2e4f7544d28a1bea00e1fdf2d1cff397b5
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50605568"
---
# <a name="additional-startup-considerations"></a>其他啟動考量

在 C++ 中，物件建構和解構可能需要執行使用者程式碼。 因此，務必了解哪些初始化發生之前項目`main`哪些解構函式結束之後叫用和`main`。 (如需建構和解構物件的詳細資訊，請參閱 <<c0> [ 建構函式](../cpp/constructors-cpp.md)並[解構函式](../cpp/destructors-cpp.md)。)

下列初始化發生之前項目以`main`:

- 靜態資料預設會初始化為零。 沒有明確初始設定式的所有靜態資料在執行其他程式碼之前會設定為零，包括執行階段初始化。 靜態資料成員仍必須明確定義。

- 初始化轉譯單位中的全域靜態物件。 這可能是因為進入`main`或之前的任何函式或物件的轉譯單位中的物件第一次使用。

**Microsoft 專屬**

在 Microsoft c + + 中，全域靜態物件會初始化進入`main`。

**結束 Microsoft 專屬**

彼此互相依存，但位於不同轉譯單位中的全域靜態物件可能會產生不正確的行為。

## <a name="see-also"></a>另請參閱

[啟動和終止](../cpp/startup-and-termination-cpp.md)