---
title: 加入屬性 （Visual c + +） |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- interfaces, adding properties
- properties [C++], adding to interfaces
ms.assetid: 37bd4db7-efd3-4faa-87ad-64902ed16a36
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 45eda098202fdf9286905bdc967b6aa1d7bd7035
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="adding-a-property-visual-c"></a>加入屬性 (Visual C++)
您可以使用[加入屬性精靈](../ide/names-add-property-wizard.md)將方法加入至您的專案中的介面。  
  
### <a name="to-add-a-property-to-your-object"></a>將屬性加入至您的物件  
  
1.  在[類別檢視](http://msdn.microsoft.com/en-us/8d7430a9-3e33-454c-a9e1-a85e3d2db925)，以滑鼠右鍵按一下您要加入屬性的介面名稱。  
  
    > [!NOTE]
    >  您也可以加入屬性的分配介面，在專案屬性，除非內沒有巢狀的程式庫節點。  
  
2.  從捷徑功能表，按一下 **新增**，然後按一下 **加入屬性**。  
  
3.  在[加入屬性精靈](../ide/names-add-property-wizard.md)，提供要建立屬性的資訊。  
  
4.  指定屬性中的任何介面定義語言 (IDL) 設定[IDL 屬性](../ide/idl-attributes-add-property-wizard.md)精靈頁面。  
  
5.  按一下**完成**以加入屬性。  
  
 **取得**和`Put`屬性方法會顯示為 [類別檢視] 中已定義的介面下方的兩個圖示。 您可以按兩下任一個圖示來檢視的屬性宣告中的.idl 檔案。  
  
-   ATL 介面**取得**和**放**函數會加入至.cpp 檔案中，並將這些函數的參考會加入的.h 檔案。  
  
-   MFC 分配介面，如果您選取**成員變數**做為實作類型，方法和變數會加入至類別實作它。 如果您選取**Get/Set 方法**做為實作類型，兩種方法會加入至類別實作它。  
  
## <a name="see-also"></a>另請參閱  
 [建立 COM 介面](../ide/creating-a-com-interface-visual-cpp.md)   
 [編輯 COM 介面](../ide/editing-a-com-interface.md)   
 [元件物件模型](http://msdn.microsoft.com/library/windows/desktop/ms694363)   
 [介面指標和介面](http://msdn.microsoft.com/library/windows/desktop/ms688484)