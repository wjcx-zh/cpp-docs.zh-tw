---
title: 功能的資料錄檢視類別 （MFC 資料存取） |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- record views, classes
- record view classes
ms.assetid: e7b2820f-09c4-483f-83c0-317e8be42bdf
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 9b6717c0ef1167e01df2f5e8de14408b23a9dbb1
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="features-of-record-view-classes--mfc-data-access"></a>記錄檢視類別的功能 (MFC 資料存取)
您可以使用類別的表單為基礎的資料存取程式設計[CFormView](../mfc/reference/cformview-class.md)，但[CRecordView](../mfc/reference/crecordview-class.md)通常是較佳的類別，以從衍生。 除了其`CFormView`功能， `CRecordView`:  
  
-   提供表單控制項和相關聯的資料錄集物件之間的對話資料交換 (DDX)。  
  
-   會處理移動第一個、 移到下一個、 移到上一個和最後移動瀏覽記錄相關聯的資料錄集物件中的命令。  
  
-   如果使用者移到另一筆記錄，更新會變更為目前的記錄。  
  
 如需瀏覽的詳細資訊，請參閱[資料錄檢視： 支援在資料錄檢視的瀏覽](../data/supporting-navigation-in-a-record-view-mfc-data-access.md)。  
  
## <a name="see-also"></a>另請參閱  
 [資料錄檢視 （MFC 資料存取）](../data/record-views-mfc-data-access.md)   
 [ODBC 驅動程式清單](../data/odbc/odbc-driver-list.md)