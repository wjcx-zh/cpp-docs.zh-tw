---
title: 使用 CArchive &lt; &lt; 和 &gt; &gt; 運算子
ms.date: 11/04/2016
helpviewer_keywords:
- objects [MFC], loading from previously stored values
- CArchive class [MFC], storing and loading objects
- CArchive class [MFC], operators
ms.assetid: 56aef326-02dc-4992-8282-f0a4b78a064e
ms.openlocfilehash: 0351cd0fad1d0fc838c75d3cdbd809a04b0fb393
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/25/2020
ms.locfileid: "88832291"
---
# <a name="using-the-carchive-ltlt-and-gtgt-operators"></a>使用 CArchive &lt; &lt; 和 &gt; &gt; 運算子

`CArchive` 提供 <\< and >> 運算子，以撰寫和讀取簡單的資料類型，以及與檔案之間的對應 `CObject` 。

#### <a name="to-store-an-object-in-a-file-via-an-archive"></a>若要透過封存將物件儲存在檔案中

1. 下列範例示範如何透過封存將物件儲存在檔案中：

   [!code-cpp[NVC_MFCSerialization#7](../mfc/codesnippet/cpp/using-the-carchive-output-and-input-operators_1.cpp)]

#### <a name="to-load-an-object-from-a-value-previously-stored-in-a-file"></a>從先前儲存在檔案中的值載入物件

1. 下列範例顯示如何從先前儲存在檔案中的值載入物件：

   [!code-cpp[NVC_MFCSerialization#8](../mfc/codesnippet/cpp/using-the-carchive-output-and-input-operators_2.cpp)]

通常，您會在衍生類別的函式中，透過封存在檔案中儲存和載入資料 `Serialize` `CObject` ，您必須使用 DECLARE_SERIALIZE 宏來宣告這些類別的功能。 物件的參考 `CArchive` 會傳遞至您的函式 `Serialize` 。 您可以呼叫物件的函式 `IsLoading` `CArchive` ，以判斷是否已呼叫函式 `Serialize` 來從檔案載入資料，或將資料儲存至檔案。

`Serialize`可序列化 `CObject` 衍生類別的函式通常具有下列形式：

[!code-cpp[NVC_MFCSerialization#9](../mfc/codesnippet/cpp/using-the-carchive-output-and-input-operators_3.cpp)]

上述程式碼範本與建立程式碼的程式碼範本完全相同， `Serialize` (一個衍生自) 的類別 `CDocument` 。 此程式碼範本可協助您撰寫更容易審視的程式碼，因為儲存程式碼和載入程式碼應該一律平行，如下列範例所示：

[!code-cpp[NVC_MFCSerialization#10](../mfc/codesnippet/cpp/using-the-carchive-output-and-input-operators_4.cpp)]

程式庫會將 **`<<`** 和運算子定義為 **`>>`** `CArchive` 第一個運算元，並將下列資料類型和類別類型定義為第二個運算元：

:::row:::
   :::column span="":::
      `BYTE`\
      `CObject*`\
      `COleCurrency`\
      `COleDateTime`\
      `COleDateTimeSpan`
   :::column-end:::
   :::column span="":::
      `COleVariant`\
      `CString`\
      `CTime` 和 `CTimeSpan`\
      `Double`
   :::column-end:::
   :::column span="":::
      `DWORD`\
      `Float`\
      `Int`\
      `LONG`
   :::column-end:::
   :::column span="":::
      `POINT` 和 `CPoint`\
      `RECT` 和 `CRect`\
      `SIZE` 和 `CSize`\
      `WORD`
   :::column-end:::
:::row-end:::

> [!NOTE]
> 透過封存儲存和載入， `CObject` 需要額外考慮。 如需詳細資訊，請參閱透過封存 [儲存和載入 CObjects](../mfc/storing-and-loading-cobjects-via-an-archive.md)。

`CArchive` **`<<`** And **`>>`** 運算子一律會傳回物件的參考 `CArchive` ，也就是第一個運算元。 這可讓您串連運算子，如下所示：

[!code-cpp[NVC_MFCSerialization#11](../mfc/codesnippet/cpp/using-the-carchive-output-and-input-operators_5.cpp)]

## <a name="see-also"></a>另請參閱

[序列化：序列化物件](../mfc/serialization-serializing-an-object.md)
