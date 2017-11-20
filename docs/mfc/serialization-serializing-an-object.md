---
title: "序列化： 序列化物件 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- serializing objects [MFC]
- serialization [MFC], objects
- objects [MFC], serializing
ms.assetid: 1db772b1-ad55-4fcf-b133-126cca082510
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 1339f7ab6b226da9f233e523171e318209e99ee4
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="serialization-serializing-an-object"></a>序列化：序列化物件
發行項[序列化： 製作可序列化類別](../mfc/serialization-making-a-serializable-class.md)示範如何讓類別能夠進行序列化。 一旦您擁有可序列化的類別，您可以將與檔案，以透過該類別的物件序列化[CArchive](../mfc/reference/carchive-class.md)物件。 本文說明：  
  
-   [什麼是 CArchive 物件](../mfc/what-is-a-carchive-object.md)。  
  
-   [建立 carchive 物件的兩種方式](../mfc/two-ways-to-create-a-carchive-object.md)。  
  
-   [如何使用 CArchive <\<和 >> 運算子](../mfc/using-the-carchive-output-and-input-operators.md)。  
  
-   [儲存及載入 CObjects 透過封存](../mfc/storing-and-loading-cobjects-via-an-archive.md)。  
  
 您可以讓架構建立可序列化文件的封存，或明確地自行建立 `CArchive` 物件。 您也可以使用可序列化的物件之間傳輸資料 <\<和 >> 運算子`CArchive`或在某些情況下，藉由呼叫`Serialize`函式的`CObject`-衍生的類別。  
  
## <a name="see-also"></a>另請參閱  
 [序列化](../mfc/serialization-in-mfc.md)

