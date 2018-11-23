---
title: 新增泛型 C++ 類別
ms.date: 11/09/2018
f1_keywords:
- vc.codewiz.classes.adding.generic
- vc.codewiz.class.generic
helpviewer_keywords:
- Visual C++, classes
- generic classes, adding
- generic classes
- generic C++ class wizard [C++]
ms.assetid: e95a5a14-dbed-4edc-8551-344fe48613cb
ms.openlocfilehash: 08ebe572da605e0f6d4d712bd7e48159598ba844
ms.sourcegitcommit: b032daf81cb5fdb1f5a988277ee30201441c4945
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/15/2018
ms.locfileid: "51694136"
---
# <a name="add-a-generic-c-class"></a>新增泛型 C++ 類別

您可以藉由使用 [類別檢視] 新增泛型 C++ 類別。 泛型 C++ 類別是您定義的類別，或是衍生自您定義類別的類別。

**將泛型 C++ 類別新增至專案：**

1. 在 [類別檢視] 中，以滑鼠右鍵按一下您要新增類別的專案，然後依序選擇 [新增] 和 [類別]。

1. 在[新增專案](../ide/add-class-dialog-box.md)對話方塊的範本窗格中，選取 [C++ 類別]。 選取 [新增]，顯示[泛型 C++ 類別精靈](#generic-c-class-wizard)。

1. 在精靈中提供類別名稱，然後定義設定，或接受預設值。

1. 若要關閉精靈並在專案中檢視新的泛型 C++ 類別，請選取 [完成]。

## <a name="in-this-section"></a>本節內容

- [泛型 C++ 類別精靈](#generic-c-class-wizard)

## <a name="generic-c-class-wizard"></a>泛型 C++ 類別精靈

將泛型 C++ 類別新增至專案。 類別不會自 ATL 或 MFC 繼承。

- **類別名稱**

  設定新類別的名稱。

- **.h 檔案**

  設定新類別的標頭檔名稱。 根據預設，此名稱是以您在 [類別名稱] 中提供的名稱為基礎。 若要將標頭檔儲存至您選擇的位置，或將類別宣告附加至現有的檔案，請選取省略符號按鈕 (**...**)。如果您指定現有的檔案並選取 [完成]，精靈會提示您指定是否應該將類別宣告附加至檔案內容。 若要附加宣告，請選取 [是]；若要返回精靈並指定另一個檔案名稱，請選取 [否]。

- **.cpp 檔**

  設定新類別的實作檔名稱。 根據預設，此名稱是以您在 [類別名稱] 中提供的名稱為基礎。 若要將實作檔儲存至您選擇的位置，或將類別定義附加至現有的檔案，請選取省略符號按鈕 (**...**)。如果您指定現有的檔案並選取 [完成]，精靈會提示您指定是否應該將類別定義附加至檔案內容。 若要附加定義，請選取 [是]；若要返回精靈並指定另一個檔案名稱，請選取 [否]。

- **基底類別**

  設定新類別的基底類別。

- **存取權**

  設定新類別的基底類別成員存取權。 存取修飾詞是指定其他類別對類別成員函式所具有之存取層級的關鍵字。 如需如何指定存取權的詳細資訊，請參閱[成員存取控制](../cpp/member-access-control-cpp.md)。 根據預設，類別存取層級會設為 `public`。

  - `public`
  - `protected`
  - `private`
  - **預設** (不會產生任何存取修飾詞)。

- **虛擬解構函式**

  指定類別解構函式是否為虛擬。 使用虛擬解構函式可協助確保在刪除衍生類別的執行個體時，會呼叫正確的解構函式。

- **內嵌**

  在標頭檔中，將類別建構函式和類別定義產生為內嵌函式。

- **受控**

  選取時，新增受控類別和標頭檔。 清除時，新增原生類別和標頭檔。
