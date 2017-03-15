---
title: "建立 CArchive 物件的兩種方式 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
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
  - "CArchive 類別, 關閉 CArchive 物件"
  - "CArchive 類別, 建構函式"
  - "CArchive 物件"
  - "CArchive 物件, 關閉"
  - "資料儲存 [C++], CArchive 類別"
  - "I/O [MFC], 建立 CArchive 物件"
  - "序列化 [C++], CArchive 類別"
  - "儲存 [C++], CArchive 類別"
ms.assetid: aefa28ce-b55c-40dc-9e42-5f038030985d
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# 建立 CArchive 物件的兩種方式
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

有兩種方法可以建立 `CArchive` 物件：  
  
-   [透過框架隱含的建立 CArchive 物件](#_core_implicit_creation_of_a_carchive_object_via_the_framework)  
  
-   [明確的建立 CArchive 物件](#_core_explicit_creation_of_a_carchive_object)  
  
##  <a name="_core_implicit_creation_of_a_carchive_object_via_the_framework"></a> 透過框架隱含的建立 CArchive 物件  
 最常見且最簡單方式，是讓架構為您的文件建立 `CArchive` 物件表示儲存，儲存為文件的和開啟檔案功能表上的命令。  
  
 以下是架構如何進行，當應用程式的使用者從檔案功能表的命令發行另存新檔:  
  
1.  顯示 \[**儲存**\] 對話方塊並從使用者取得這個檔名。  
  
2.  以 `CFile` 物件開啟使用者命名的檔案。  
  
3.  建立指向這個 `CFile` 物件的 `CArchive` 物件。  在建立 `CArchive` 物件，架構設定模式「儲存」\(寫入，序列化\)，與「載入」\(讀取，序列化\) 相反。  
  
4.  呼叫定義自您的 **CDocument** 衍生類別的 `Serialize` 函式，傳遞它 `CArchive` 物件的參考。  
  
 您的文件的 `Serialize` 函式將資料寫入至 `CArchive` 物件，如之後的簡短說明一般。  在從 `Serialize` 函式傳回時，這個框架終結 `CArchive` 物件和 `CFile` 物件。  
  
 因此，如果您讓架構建立文件的 `CArchive` 物件，您只需要實作來回封存寫入和讀取文件的 `Serialize` 函式。  您也必須實作所有文件的 `Serialize` 函式直接或間接接著序列化 `CObject` 衍生物件的 `Serialize`。  
  
##  <a name="_core_explicit_creation_of_a_carchive_object"></a> 明確的建立 CArchive 物件  
 除了透過架構序列化，您可能有其他場合需要 `CArchive` 物件。  例如，您可能會想來回序列化剪貼簿中的資料，由 `CSharedFile` 物件表示。  或者，您可能想要使用儲存不同於架構提供的檔案的使用使用者介面。  在這種情況下，您可以明確建立 `CArchive` 物件。  使用下列程序，這樣做與架構方式相同。  
  
#### 明確建立 CArchive 物件  
  
1.  建立 `CFile`或從 `CFile` 衍生的物件。  
  
2.  如下列範例所示，傳遞 `CFile` 物件至建構函式給 `CArchive`:  
  
     [!code-cpp[NVC_MFCSerialization#5](../mfc/codesnippet/CPP/two-ways-to-create-a-carchive-object_1.cpp)]  
  
     傳遞給 `CArchive` 建構函式的第二個引數是指定的列舉值指定是否為儲存或載入資料會使用來回檔案。  `Serialize` 函式會為封存物件呼叫 `IsStoring` 函式來檢查這個狀態的物件。  
  
 當您完成從或往 `CArchive` 物件儲存或載入，請將其關閉。  雖然 `CArchive` \(和 `CFile`\) 物件會自動關閉封存 \(和檔案\)，最好先明確如此，因為從錯誤復原更加容易。  如需錯誤處理的詳細資訊，請參閱本文件的 [例外狀況:攔截和刪除例外狀況](../mfc/exceptions-catching-and-deleting-exceptions.md)。  
  
#### 關閉 CArchive 物件  
  
1.  下列範例示範如何關閉 `CArchive` 物件。  
  
     [!code-cpp[NVC_MFCSerialization#6](../mfc/codesnippet/CPP/two-ways-to-create-a-carchive-object_2.cpp)]  
  
## 請參閱  
 [序列化：序列化物件](../mfc/serialization-serializing-an-object.md)