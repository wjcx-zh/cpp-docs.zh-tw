---
title: 泛型 C++ 類別精靈 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
f1_keywords:
- vc.codewiz.class.generic
dev_langs:
- C++
helpviewer_keywords:
- Generic C++ Class Wizard [C++]
ms.assetid: aa95be9e-fc1b-45db-a11d-0d32c4929077
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 7b104c0631fde3164ef4299cead47caba912874b
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46431082"
---
# <a name="generic-c-class-wizard"></a>泛型 C++ 類別精靈

將泛型 C++ 類別新增至專案。 類別不會從 ATL 或 MFC 繼承。

- **類別名稱**

   設定新類別的名稱。

- **.h 檔案**

   設定新類別的標頭檔名稱。 根據預設，此名稱是以您在 [類別名稱] 中提供的名稱為基礎。 若要將標頭檔儲存至您選擇的位置，或將類別宣告附加至現有的檔案，請按一下省略符號按鈕 (**...**)。如果您指定現有的檔案，當您按一下 [完成] 時，精靈會提示您指定是否應該將類別宣告附加至檔案的內容。 若要附加宣告，請按一下 [是]；若要返回精靈並指定另一個檔案名稱，請按一下 [否]。

- **.cpp 檔案**

   設定新類別的實作檔名稱。 根據預設，此名稱是以您在 [類別名稱] 中提供的名稱為基礎。 若要將實作檔儲存至您選擇的位置，或將類別定義附加至現有的檔案，請按一下省略符號按鈕 (**...**)。如果您指定現有的檔案，當您按一下 [完成] 時，精靈會提示您指定是否應該將類別定義附加至檔案的內容。 若要附加定義，請按一下 [是]；若要返回精靈並指定另一個檔案名稱，請按一下 [否]。

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

- **Inline**

   在標頭檔中，將類別建構函式和類別定義產生為內嵌函式。

- **受控**

   選取時，新增受控類別和標頭檔。 清除時，新增原生類別和標頭檔。

## <a name="see-also"></a>請參閱

[新增泛型 C++ 類別](../ide/adding-a-generic-cpp-class.md)