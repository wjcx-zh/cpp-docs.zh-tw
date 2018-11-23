---
title: 覆寫虛擬函式
ms.date: 11/12/2018
f1_keywords:
- vc.codewiz.virtualfunc.override
helpviewer_keywords:
- virtual functions, overriding
- base classes, overriding virtual functions defined in
- Properties window, overriding virtual functions in
ms.assetid: 2d8c76f2-7a6b-4c9c-8de5-4282ce7755b6
ms.openlocfilehash: 9bb3fd34bbfa14cce1595ed586c4e1b66518e7b7
ms.sourcegitcommit: b032daf81cb5fdb1f5a988277ee30201441c4945
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/15/2018
ms.locfileid: "51694019"
---
# <a name="override-a-virtual-function"></a>覆寫虛擬函式

您可以從 Visual Studio [屬性視窗](/visualstudio/ide/reference/properties-window)覆寫基底類別中定義的虛擬函式。

**在 [屬性] 視窗中覆寫虛擬函式：**

1. 在 [類別檢視] 中，選取類別。

1. 在 [屬性] 視窗中，選取 [覆寫] 按鈕。

   > [!NOTE]
   > 當您在 [類別檢視] 中選取類別名稱或在原始檔視窗內選取時，即可使用 [覆寫] 按鈕。

   左欄會列出虛擬函式。 如果某個虛擬函式的名稱也出現在右欄，則已實作覆寫。

1. 如果函式沒有覆寫，則選取 [屬性] 視窗右側資料行中的資料格，將函式覆寫的建議名稱顯示為 \<add>*FuncName*。

1. 選取建議名稱，新增函式的虛設常式程式碼。

1. 若要編輯覆寫函式，請按兩下 [類別檢視] 中的函式名稱，然後在原始檔視窗中編輯程式碼。

若要移除覆寫，請選取右側資料行中的覆寫函式名稱，然後選取 \<delete>*FuncName*。 這會將函式的程式碼標記為註解。
