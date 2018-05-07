---
title: 建立 CArchive 物件的兩種方式 |Microsoft 文件
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
- CArchive class [MFC], closing CArchive objects
- CArchive objects [MFC], closing
- I/O [MFC], creating CArchive objects
- serialization [MFC], CArchive class
- CArchive objects [MFC]
- storage [MFC], CArchive class [MFC]
- data storage [MFC], CArchive class
- CArchive class [MFC], constructor
ms.assetid: aefa28ce-b55c-40dc-9e42-5f038030985d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 87abaa5a3564c61a6944e0cc31e81375f92a3a80
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="two-ways-to-create-a-carchive-object"></a>建立 CArchive 物件的兩種方式
建立 `CArchive` 物件的方法有兩種：  
  
-   [隱含建立 CArchive 物件透過架構](#_core_implicit_creation_of_a_carchive_object_via_the_framework)  
  
-   [明確建立 CArchive 物件](#_core_explicit_creation_of_a_carchive_object)  
  
##  <a name="_core_implicit_creation_of_a_carchive_object_via_the_framework"></a> 隱含建立 CArchive 物件透過架構  
 最常見且簡單的方法，方法是讓架構建立`CArchive`代表儲存、 另存新檔，和開啟檔案 功能表命令的文件的物件。  
  
 以下是架構的功能當應用程式的使用者發出 Save As 命令，從 [檔案] 功能表：  
  
1.  呈現**存** 對話方塊，並從使用者取得檔案名稱。  
  
2.  開啟檔案命名為使用者`CFile`物件。  
  
3.  建立`CArchive`指向這個物件`CFile`物件。 在建立`CArchive`物件，此架構將模式設定為 [儲存] 寫入 (序列化），而不是 [載入] （讀取、 還原序列化）。  
  
4.  呼叫`Serialize`函式定義於您**CDocument**-衍生的類別，將的參考傳遞`CArchive`物件。  
  
 您的文件`Serialize`函式接著會將資料寫入`CArchive`物件，如稍後說明。 傳回從時您`Serialize`函式，架構會終結`CArchive`物件，然後`CFile`物件。  
  
 因此，如果您讓架構建立`CArchive`物件文件時，您只需要為實作的文件`Serialize`寫入和讀取與封存的函式。 您也必須實作`Serialize`任何`CObject`-衍生物件的文件的`Serialize`直接或間接，接著將序列化函式。  
  
##  <a name="_core_explicit_creation_of_a_carchive_object"></a> 明確建立 CArchive 物件  
 除了序列化架構透過文件，有其他情況下，您可能需要`CArchive`物件。 例如，您可能要序列化資料以及從剪貼簿，並由`CSharedFile`物件。 或者，您可以用來儲存的檔案，不同於架構所提供的使用者介面。 在此情況下，您可以明確地建立`CArchive`物件。 這麼做的相同方式，架構會做，請使用下列程序。  
  
#### <a name="to-explicitly-create-a-carchive-object"></a>若要明確地建立 CArchive 物件  
  
1.  建構`CFile`物件衍生自`CFile`。  
  
2.  傳遞`CFile`物件的建構函式`CArchive`，如下列範例所示：  
  
     [!code-cpp[NVC_MFCSerialization#5](../mfc/codesnippet/cpp/two-ways-to-create-a-carchive-object_1.cpp)]  
  
     第二個引數`CArchive`建構函式是一個列舉的值，指定是否將對檔案中儲存或載入資料或使用封存。 `Serialize`函式物件的呼叫來檢查此狀態`IsStoring`保存物件的函式。  
  
 當您完成儲存或載入資料，或從`CArchive`物件，請將它關閉。 雖然`CArchive`(和`CFile`) 物件會自動關閉封存 （和檔案），它是很好的作法，明確地進行操作，因為這樣會讓從錯誤中的復原更容易。 如需有關錯誤處理的詳細資訊，請參閱文章[例外狀況： 攔截及刪除例外狀況](../mfc/exceptions-catching-and-deleting-exceptions.md)。  
  
#### <a name="to-close-the-carchive-object"></a>若要關閉 CArchive 物件  
  
1.  下列範例說明如何關閉`CArchive`物件：  
  
     [!code-cpp[NVC_MFCSerialization#6](../mfc/codesnippet/cpp/two-ways-to-create-a-carchive-object_2.cpp)]  
  
## <a name="see-also"></a>另請參閱  
 [序列化：序列化物件](../mfc/serialization-serializing-an-object.md)

