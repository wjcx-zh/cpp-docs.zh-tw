---
title: "功能的資料錄檢視類別 （MFC 資料存取） |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- record views, classes
- record view classes
ms.assetid: e7b2820f-09c4-483f-83c0-317e8be42bdf
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 1c975aac0459a13a3fb95fdec3dff1a648b0efec
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="features-of-record-view-classes--mfc-data-access"></a>記錄檢視類別的功能 (MFC 資料存取)
您可以使用類別的表單為基礎的資料存取程式設計[CFormView](../mfc/reference/cformview-class.md)，但[CRecordView](../mfc/reference/crecordview-class.md)通常是較佳的類別，以從衍生。 除了其`CFormView`功能， `CRecordView`:  
  
-   提供表單控制項和相關聯的資料錄集物件之間的對話資料交換 (DDX)。  
  
-   會處理移動第一個、 移到下一個、 移到上一個和最後移動瀏覽記錄相關聯的資料錄集物件中的命令。  
  
-   如果使用者移到另一筆記錄，更新會變更為目前的記錄。  
  
 如需瀏覽的詳細資訊，請參閱[資料錄檢視： 支援在資料錄檢視的瀏覽](../data/supporting-navigation-in-a-record-view-mfc-data-access.md)。  
  
## <a name="see-also"></a>請參閱  
 [資料錄檢視 （MFC 資料存取）](../data/record-views-mfc-data-access.md)   
 [ODBC 驅動程式清單](../data/odbc/odbc-driver-list.md)