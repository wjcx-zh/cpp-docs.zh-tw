---
title: 建立 CArchive 物件的兩種方式
ms.date: 11/04/2016
helpviewer_keywords:
- CArchive class [MFC], closing CArchive objects
- CArchive objects [MFC], closing
- I/O [MFC], creating CArchive objects
- serialization [MFC], CArchive class
- CArchive objects [MFC]
- storage [MFC], CArchive class [MFC]
- data storage [MFC], CArchive class
- CArchive class [MFC], constructor
ms.assetid: aefa28ce-b55c-40dc-9e42-5f038030985d
ms.openlocfilehash: 38642906b0973730149ed0de5381519f06d69fe5
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/17/2020
ms.locfileid: "79442034"
---
# <a name="two-ways-to-create-a-carchive-object"></a>建立 CArchive 物件的兩種方式

建立 `CArchive` 物件的方法有兩種：

- [透過架構隱含建立 CArchive 物件](#_core_implicit_creation_of_a_carchive_object_via_the_framework)

- [CArchive 物件的明確建立](#_core_explicit_creation_of_a_carchive_object)

##  <a name="_core_implicit_creation_of_a_carchive_object_via_the_framework"></a>透過架構隱含建立 CArchive 物件

最常見且最簡單的方式是讓架構代表 [檔案] 功能表上的 [儲存]、[另存新檔] 和 [開啟] 命令，建立檔的 `CArchive` 物件。

以下是當您的應用程式使用者從 [檔案] 功能表發出 [另存新檔] 命令時，該架構的作用：

1. 顯示 [**另存**新檔] 對話方塊，並取得使用者的檔案名。

1. 將使用者所命名的檔案以 `CFile` 物件的形式開啟。

1. 建立指向這個 `CFile` 物件的 `CArchive` 物件。 在建立 `CArchive` 物件時，架構會將模式設定為「存放」（寫入、序列化），而不是「載入」（讀取、還原序列化）。

1. 呼叫 `CDocument`衍生類別中定義的 `Serialize` 函式，並傳遞 `CArchive` 物件的參考。

您的檔 `Serialize` 函式接著會將資料寫入 `CArchive` 物件，如稍後所述。 從您的 `Serialize` 函式傳回時，架構會先終結 `CArchive` 物件，然後再終結 `CFile` 物件。

因此，如果您讓架構建立檔的 `CArchive` 物件，您只需要執行檔的 `Serialize` 函式，以便在封存中寫入和讀取。 您也必須針對檔的 `Serialize` 函式直接或間接序列化的任何 `CObject`衍生物件，執行 `Serialize`。

##  <a name="_core_explicit_creation_of_a_carchive_object"></a>CArchive 物件的明確建立

除了透過架構來序列化檔以外，還有其他的時候，您可能需要 `CArchive` 物件。 例如，您可能想要將資料從剪貼簿序列化，並以 `CSharedFile` 物件表示。 或者，您可能會想要使用使用者介面來儲存與架構所提供的檔案不同的檔案。 在此情況下，您可以明確地建立 `CArchive` 物件。 您可以使用下列程式，以與架構相同的方式來執行這項操作。

#### <a name="to-explicitly-create-a-carchive-object"></a>明確建立 CArchive 物件

1. 建立 `CFile` 物件或衍生自 `CFile`的物件。

1. 將 `CFile` 物件傳遞至 `CArchive`的函式，如下列範例所示：

   [!code-cpp[NVC_MFCSerialization#5](../mfc/codesnippet/cpp/two-ways-to-create-a-carchive-object_1.cpp)]

   `CArchive` 的函式的第二個引數是列舉值，指定是否要使用封存來儲存或從檔案載入資料。 物件的 `Serialize` 函式會藉由呼叫 archive 物件的 `IsStoring` 函數來檢查此狀態。

當您完成在 `CArchive` 物件中儲存或載入資料時，請將其關閉。 雖然 `CArchive` （和 `CFile`）物件會自動關閉封存（和檔案），但最好是明確地這麼做，因為它可讓您更輕鬆地從錯誤復原。 如需有關錯誤處理的詳細資訊，請參閱[例外狀況：攔截及刪除例外](../mfc/exceptions-catching-and-deleting-exceptions.md)狀況。

#### <a name="to-close-the-carchive-object"></a>關閉 CArchive 物件

1. 下列範例說明如何關閉 `CArchive` 物件：

   [!code-cpp[NVC_MFCSerialization#6](../mfc/codesnippet/cpp/two-ways-to-create-a-carchive-object_2.cpp)]

## <a name="see-also"></a>另請參閱

[序列化：序列化物件](../mfc/serialization-serializing-an-object.md)
