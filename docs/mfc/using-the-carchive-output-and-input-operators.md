---
title: "使用 CArchive &lt;&lt; 和 &gt;&gt; 運算子 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CArchive"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CArchive 類別, 運算子"
  - "CArchive 類別, 儲存及載入物件"
  - "物件 [C++], 從先前儲存的值載入"
ms.assetid: 56aef326-02dc-4992-8282-f0a4b78a064e
caps.latest.revision: 10
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 使用 CArchive &lt;&lt; 和 &gt;&gt; 運算子
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

`CArchive` 提供 \<\< 和 \>\> 運算子撰寫和讀取簡單資料型別以及 `CObject`來回檔案。  
  
#### 儲存物件在檔案中的封存  
  
1.  下列範例會在檔案顯示如何儲存物件透過封存:  
  
     [!code-cpp[NVC_MFCSerialization#7](../mfc/codesnippet/CPP/using-the-carchive-output-and-input-operators_1.cpp)]  
  
#### 從檔案先前儲存的值載入物件。  
  
1.  下列範例示範如何從檔案先前儲存的值載入物件:  
  
     [!code-cpp[NVC_MFCSerialization#8](../mfc/codesnippet/CPP/using-the-carchive-output-and-input-operators_2.cpp)]  
  
 通常，您將檔案儲存和載入傳遞資料保存在 `CObject`的 `Serialize` 函式衍生類別，您必須宣告與 **DECLARE\_SERIALIZE** 巨集。  對 `CArchive` 物件的參考傳遞至 `Serialize` 函式。  您呼叫 `CArchive` 物件的 `IsLoading` 函式來判斷 `Serialize` 函式是否呼叫從檔案載入資料或將資料儲存至檔案。  
  
 可序列化之 `CObject`的 `Serialize` 函式衍生類別通常會具有下列格式:  
  
 [!code-cpp[NVC_MFCSerialization#9](../mfc/codesnippet/CPP/using-the-carchive-output-and-input-operators_3.cpp)]  
  
 上述程式碼範本完全做為文件的 `Serialize` 函式中的 AppWizard 建立相同 \( **CDocument\)**從類別衍生自。  這個程式碼範本可協助您撰寫更容易在下列範例中檢閱的程式碼，因為存放的程式碼和載入程式碼必須是平行:  
  
 [!code-cpp[NVC_MFCSerialization#10](../mfc/codesnippet/CPP/using-the-carchive-output-and-input-operators_4.cpp)]  
  
 程式庫定義 **\<\<** 和 **\>\>** `CArchive` 的運算子做為第一個運算元和下列資料型別和類別型別做為第二個運算元:  
  
||||  
|-|-|-|  
|`CObject*`|**大小和 CSize**|**float**|  
|**WORD**|`CString`|**POINT** 和 `CPoint`|  
|`DWORD`|**BYTE**|`RECT` 和 `CRect`|  
|**Double**|**LONG**|`CTime` 和 `CTimeSpan`|  
|`Int`|**COleCurrency**|`COleVariant`|  
|`COleDateTime`|`COleDateTimeSpan`||  
  
> [!NOTE]
>  藉由封存儲存和載入 `CObject` 需要額外的考量。  如需詳細資訊，請參閱 [儲存和載入 CObjects 透過封存](../mfc/storing-and-loading-cobjects-via-an-archive.md)。  
  
 **CArchive \<\<** 和 **\>\>** 運算子一律傳回 `CArchive` 物件的參考，是第一個運算元。  這可讓您繫結運算子，如下所示:  
  
 [!code-cpp[NVC_MFCSerialization#11](../mfc/codesnippet/CPP/using-the-carchive-output-and-input-operators_5.cpp)]  
  
## 請參閱  
 [序列化：序列化物件](../mfc/serialization-serializing-an-object.md)