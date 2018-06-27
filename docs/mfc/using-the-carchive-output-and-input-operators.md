---
title: 使用 CArchive &lt; &lt;和&gt;&gt;運算子 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- CArchive
dev_langs:
- C++
helpviewer_keywords:
- objects [MFC], loading from previously stored values
- CArchive class [MFC], storing and loading objects
- CArchive class [MFC], operators
ms.assetid: 56aef326-02dc-4992-8282-f0a4b78a064e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 617157c3adce8521eb54156988cb098c0e709fd2
ms.sourcegitcommit: c6b095c5f3de7533fd535d679bfee0503e5a1d91
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/26/2018
ms.locfileid: "36953281"
---
# <a name="using-the-carchive-ltlt-and-gtgt-operators"></a>使用 CArchive &lt; &lt;和&gt;&gt;運算子
`CArchive` 提供 <\<和 >> 用於寫入和讀取簡單資料類型的運算子以及`CObject`s 和檔案。  
  
#### <a name="to-store-an-object-in-a-file-via-an-archive"></a>若要透過封存之檔案中儲存物件  
  
1.  下列範例會示範如何透過封存之檔案中儲存物件：  
  
     [!code-cpp[NVC_MFCSerialization#7](../mfc/codesnippet/cpp/using-the-carchive-output-and-input-operators_1.cpp)]  
  
#### <a name="to-load-an-object-from-a-value-previously-stored-in-a-file"></a>若要載入的物件自先前儲存在檔案中的值  
  
1.  下列範例會示範如何載入的物件自先前儲存在檔案中的值：  
  
     [!code-cpp[NVC_MFCSerialization#8](../mfc/codesnippet/cpp/using-the-carchive-output-and-input-operators_2.cpp)]  
  
 通常，儲存和載入資料以及從透過在封存檔案`Serialize`函式的`CObject`-衍生的類別，您必須已經宣告與 DECLARE_SERIALIZE 巨集。 若要參考`CArchive`物件傳遞至您`Serialize`函式。 您呼叫`IsLoading`函式的`CArchive`物件，以判斷是否`Serialize`被呼叫函式，從檔案載入資料，或將資料儲存到檔案。  
  
 `Serialize`函式的可序列化`CObject`-衍生的類別通常具有下列格式：  
  
 [!code-cpp[NVC_MFCSerialization#9](../mfc/codesnippet/cpp/using-the-carchive-output-and-input-operators_3.cpp)]  
  
 上述程式碼範本正好一個 AppWizard 建立的相同`Serialize`函式的文件 (的類別衍生自`CDocument`)。 這個程式碼範本可協助您撰寫程式碼，更輕鬆地檢視，因為儲存的程式碼並載入程式碼應該是平行進行，如下列範例所示：  
  
 [!code-cpp[NVC_MFCSerialization#10](../mfc/codesnippet/cpp/using-the-carchive-output-and-input-operators_4.cpp)]  
  
 程式庫會定義**< \<** 和**>>** 運算子`CArchive`做為第一個運算元的下列資料類型和類別做為第二個運算元的類型:  
  
||||  
|-|-|-|  
|`CObject*`|**大小**和 `CSize`|**float**|  
|**WORD**|`CString`|**點**和 `CPoint`|  
|`DWORD`|**BYTE**|`RECT` 和 `CRect`|  
|**Double**|**LONG**|`CTime` 和 `CTimeSpan`|  
|`Int`|**COleCurrency**|`COleVariant`|  
|`COleDateTime`|`COleDateTimeSpan`||  
  
> [!NOTE]
>  儲存及載入`CObject`透過封存 s 需要額外的考量。 如需詳細資訊，請參閱[儲存和載入 CObjects 透過封存](../mfc/storing-and-loading-cobjects-via-an-archive.md)。  
  
 **CArchive <\<** 和**>>** 運算子一律會傳回參考`CArchive`物件，它是第一個運算元。 這可讓您將運算子鍊結，如下所示：  
  
 [!code-cpp[NVC_MFCSerialization#11](../mfc/codesnippet/cpp/using-the-carchive-output-and-input-operators_5.cpp)]  
  
## <a name="see-also"></a>另請參閱  
 [序列化：序列化物件](../mfc/serialization-serializing-an-object.md)

