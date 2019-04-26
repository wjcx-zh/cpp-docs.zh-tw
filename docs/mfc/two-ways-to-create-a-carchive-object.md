---
title: 建立 CArchive 物件的兩種方式
ms.date: 11/04/2016
f1_keywords:
- CArchive
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
ms.openlocfilehash: 80e3e73840bce53691c3f5fdafb62c60bdb8f832
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62181506"
---
# <a name="two-ways-to-create-a-carchive-object"></a>建立 CArchive 物件的兩種方式

建立 `CArchive` 物件的方法有兩種：

- [隱含建立透過 framework CArchive 物件](#_core_implicit_creation_of_a_carchive_object_via_the_framework)

- [明確建立 CArchive 物件](#_core_explicit_creation_of_a_carchive_object)

##  <a name="_core_implicit_creation_of_a_carchive_object_via_the_framework"></a> 隱含建立透過 Framework CArchive 物件

最常見且最簡單的方式是讓架構建立`CArchive`物件代表儲存、 另存新檔，並開啟的命令，在 [檔案] 功能表上的文件。

以下是什麼架構也是當應用程式的使用者發出從 [檔案] 功能表的 [另存新檔] 命令：

1. 呈現**另存新檔** 對話方塊中，並從使用者取得檔案名稱。

1. 開啟檔案的使用者，作為名為`CFile`物件。

1. 會建立`CArchive`物件，這會指向`CFile`物件。 建立`CArchive`物件時，架構會設定 「 儲存 」 的模式 （寫入、 序列化），而不是 「 載入 」 （讀取、 還原序列化）。

1. 呼叫`Serialize`函式中定義您`CDocument`-衍生的類別，它參考傳遞給`CArchive`物件。

您的文件`Serialize`函式接著會將資料寫入`CArchive`物件，如稍後說明。 傳回從時您`Serialize`函式，此架構會終結`CArchive`物件，然後`CFile`物件。

因此，如果您讓架構建立`CArchive`物件的文件時，您只需要實作的文件`Serialize`寫入和讀取封存的來回函式。 您也必須實作`Serialize`任何`CObject`-衍生物件的文件的`Serialize`函式接著會序列化直接或間接。

##  <a name="_core_explicit_creation_of_a_carchive_object"></a> 明確建立 CArchive 物件

除了序列化透過 framework 文件，有其他有時候，您可能需要`CArchive`物件。 比方說，您可能想要將資料從剪貼簿，並由來回序列化`CSharedFile`物件。 或者，您可能想要使用使用者介面，來儲存不同架構所提供的檔案。 在此情況下，您可以明確地建立`CArchive`物件。 這麼做的相同方式，架構也是，使用下列程序。

#### <a name="to-explicitly-create-a-carchive-object"></a>若要明確地建立 CArchive 物件

1. 建構`CFile`物件衍生自`CFile`。

1. 傳遞`CFile`物件的建構函式`CArchive`，如下列範例所示：

   [!code-cpp[NVC_MFCSerialization#5](../mfc/codesnippet/cpp/two-ways-to-create-a-carchive-object_1.cpp)]

   第二個引數`CArchive`建構函式是一個列舉的值，指定是否會對檔案中儲存或載入資料或使用封存。 `Serialize`函式，物件會檢查此狀態，藉由呼叫`IsStoring`封存物件的函式。

當您完成儲存或載入資料或從`CArchive`物件、 將它關閉。 雖然`CArchive`(和`CFile`) 封存 （和檔案），將會自動關閉物件，它是很好的作法明確因為讓從錯誤復原更為容易。 如需有關錯誤處理的詳細資訊，請參閱[例外狀況：攔截及刪除例外狀況](../mfc/exceptions-catching-and-deleting-exceptions.md)。

#### <a name="to-close-the-carchive-object"></a>關閉 CArchive 物件

1. 下列範例說明如何關閉`CArchive`物件：

   [!code-cpp[NVC_MFCSerialization#6](../mfc/codesnippet/cpp/two-ways-to-create-a-carchive-object_2.cpp)]

## <a name="see-also"></a>另請參閱

[序列化：序列化物件](../mfc/serialization-serializing-an-object.md)
