---
title: 使用 CArchive &lt;&lt; 和 &gt;&gt; 運算子
ms.date: 11/04/2016
helpviewer_keywords:
- objects [MFC], loading from previously stored values
- CArchive class [MFC], storing and loading objects
- CArchive class [MFC], operators
ms.assetid: 56aef326-02dc-4992-8282-f0a4b78a064e
ms.openlocfilehash: 8e175f35f2218341c69571c818711596180df4a6
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/17/2020
ms.locfileid: "79442183"
---
# <a name="using-the-carchive-ltlt-and-gtgt-operators"></a>使用 CArchive &lt;&lt; 和 &gt;&gt; 運算子

`CArchive` 提供 <\< 和 > > 運算子，以寫入和讀取簡單的資料類型，以及與檔案之間的 `CObject`。

#### <a name="to-store-an-object-in-a-file-via-an-archive"></a>透過封存將物件儲存在檔案中

1. 下列範例示範如何透過封存將物件儲存在檔案中：

   [!code-cpp[NVC_MFCSerialization#7](../mfc/codesnippet/cpp/using-the-carchive-output-and-input-operators_1.cpp)]

#### <a name="to-load-an-object-from-a-value-previously-stored-in-a-file"></a>若要從先前儲存在檔案中的值載入物件

1. 下列範例顯示如何從先前儲存在檔案中的值載入物件：

   [!code-cpp[NVC_MFCSerialization#8](../mfc/codesnippet/cpp/using-the-carchive-output-and-input-operators_2.cpp)]

通常，您會透過 `CObject`衍生類別之 `Serialize` 函式中的封存，在檔案中儲存和載入資料，而您必須使用 DECLARE_SERIALIZE 宏來宣告此功能。 `CArchive` 物件的參考會傳遞至您的 `Serialize` 函數。 您可以呼叫 `CArchive` 物件的 `IsLoading` 函式，以判斷是否已呼叫 `Serialize` 函數從檔案載入資料，或將資料儲存至檔案。

可序列化 `CObject`衍生類別的 `Serialize` 函式通常具有下列格式：

[!code-cpp[NVC_MFCSerialization#9](../mfc/codesnippet/cpp/using-the-carchive-output-and-input-operators_3.cpp)]

上述程式碼範本與在檔的 `Serialize` 函式（衍生自 `CDocument`的類別）中建立的工作，完全相同。 這個程式碼範本可協助您撰寫更容易審查的程式碼，因為儲存程式碼和載入的程式碼應該一律平行，如下列範例所示：

[!code-cpp[NVC_MFCSerialization#10](../mfc/codesnippet/cpp/using-the-carchive-output-and-input-operators_4.cpp)]

程式庫會將 `CArchive` 的 **<\<** 和 **>>** 運算子定義為第一個運算元，並將下列資料類型和類別類型當做第二個運算元：

||||
|-|-|-|
|`CObject*`|**大小**和 `CSize`|**float**|
|**WORD**|`CString`|**POINT**和 `CPoint`|
|`DWORD`|**BYTE**|`RECT` 和 `CRect`|
|**Double**|**LONG**|`CTime` 和 `CTimeSpan`|
|`Int`|**COleCurrency**|`COleVariant`|
|`COleDateTime`|`COleDateTimeSpan`||

> [!NOTE]
>  透過封存儲存和載入 `CObject`，需要額外的考慮。 如需詳細資訊，請參閱透過封存[儲存和載入 CObjects](../mfc/storing-and-loading-cobjects-via-an-archive.md)。

**CArchive <\<** 和 **>>** 運算子一律會傳回 `CArchive` 物件的參考，也就是第一個運算元。 這可讓您連鎖運算子，如下所示：

[!code-cpp[NVC_MFCSerialization#11](../mfc/codesnippet/cpp/using-the-carchive-output-and-input-operators_5.cpp)]

## <a name="see-also"></a>另請參閱

[序列化：序列化物件](../mfc/serialization-serializing-an-object.md)
