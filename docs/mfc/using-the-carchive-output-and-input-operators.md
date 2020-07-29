---
title: 使用 CArchive &lt; &lt; 和 &gt; &gt; 運算子
ms.date: 11/04/2016
helpviewer_keywords:
- objects [MFC], loading from previously stored values
- CArchive class [MFC], storing and loading objects
- CArchive class [MFC], operators
ms.assetid: 56aef326-02dc-4992-8282-f0a4b78a064e
ms.openlocfilehash: 5029227078ac0af9ebdd0c74522a7b0ae8ea4d42
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87228514"
---
# <a name="using-the-carchive-ltlt-and-gtgt-operators"></a>使用 CArchive &lt; &lt; 和 &gt; &gt; 運算子

`CArchive`提供 <\< and >> 運算子，以寫入和讀取簡單的資料類型，以及與檔案之間的對應 `CObject` 。

#### <a name="to-store-an-object-in-a-file-via-an-archive"></a>透過封存將物件儲存在檔案中

1. 下列範例示範如何透過封存將物件儲存在檔案中：

   [!code-cpp[NVC_MFCSerialization#7](../mfc/codesnippet/cpp/using-the-carchive-output-and-input-operators_1.cpp)]

#### <a name="to-load-an-object-from-a-value-previously-stored-in-a-file"></a>若要從先前儲存在檔案中的值載入物件

1. 下列範例顯示如何從先前儲存在檔案中的值載入物件：

   [!code-cpp[NVC_MFCSerialization#8](../mfc/codesnippet/cpp/using-the-carchive-output-and-input-operators_2.cpp)]

通常，您會在衍生類別的函式中，透過封存來儲存和載入檔案中的資料， `Serialize` `CObject` 您必須使用 DECLARE_SERIALIZE 宏來宣告這些功能。 物件的參考 `CArchive` 會傳遞至您的函式 `Serialize` 。 您可以呼叫物件的函式 `IsLoading` `CArchive` ，以判斷是否已呼叫函式 `Serialize` 以從檔案載入資料，或將資料儲存至檔案。

`Serialize`可序列化 `CObject` 衍生類別的功能通常具有下列格式：

[!code-cpp[NVC_MFCSerialization#9](../mfc/codesnippet/cpp/using-the-carchive-output-and-input-operators_3.cpp)]

上述程式碼範本與在檔的函式 `Serialize` （衍生自的類別）的功能所建立的相同 `CDocument` 。 這個程式碼範本可協助您撰寫更容易審查的程式碼，因為儲存程式碼和載入的程式碼應該一律平行，如下列範例所示：

[!code-cpp[NVC_MFCSerialization#10](../mfc/codesnippet/cpp/using-the-carchive-output-and-input-operators_4.cpp)]

程式庫會將運算子定義為 **<\<** and **>>** `CArchive` 第一個運算元，並將下列資料類型和類別類型當做第二個運算元：

||||
|-|-|-|
|`CObject*`|**大小**和`CSize`|**`float`**|
|**斷**|`CString`|**點**和`CPoint`|
|`DWORD`|**節**|`RECT` 和 `CRect`|
|**Double**|**前提**|`CTime` 和 `CTimeSpan`|
|`Int`|**COleCurrency**|`COleVariant`|
|`COleDateTime`|`COleDateTimeSpan`||

> [!NOTE]
> 透過封存儲存和載入， `CObject` 需要額外的考慮。 如需詳細資訊，請參閱透過封存[儲存和載入 CObjects](../mfc/storing-and-loading-cobjects-via-an-archive.md)。

**CArchive <\<** and **> > **運算子一律會傳回物件的參考，也 `CArchive` 就是第一個運算元。 這可讓您連鎖運算子，如下所示：

[!code-cpp[NVC_MFCSerialization#11](../mfc/codesnippet/cpp/using-the-carchive-output-and-input-operators_5.cpp)]

## <a name="see-also"></a>另請參閱

[序列化：序列化物件](../mfc/serialization-serializing-an-object.md)
