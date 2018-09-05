---
title: 新增屬性 (Visual C++) | Microsoft Docs
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
ms.openlocfilehash: 00b19fa7166e6edad05d729c5a738a2a827086ae
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/29/2018
ms.locfileid: "43212791"
---
# <a name="adding-a-property-visual-c"></a>加入屬性 (Visual C++)
您可以使用[新增屬性精靈](../ide/names-add-property-wizard.md)將方法新增至專案中的介面。  
  
### <a name="to-add-a-property-to-your-object"></a>將屬性新增至您的物件  
  
1.  在[類別檢視](https://msdn.microsoft.com/8d7430a9-3e33-454c-a9e1-a85e3d2db925)中，以滑鼠右鍵按一下您要新增屬性的介面名稱。  
  
    > [!NOTE]
    >  您也可以將屬性新增至分配介面，除非專案有屬性，否則它會巢狀位於程式庫節點內。  
  
2.  從捷徑功能表按一下 [新增]，然後按一下 [新增屬性]。  
  
3.  在[新增屬性精靈](../ide/names-add-property-wizard.md)中，提供建立屬性用的資訊。  
  
4.  在精靈的 [IDL 屬性](../ide/idl-attributes-add-property-wizard.md)頁面中，指定屬性的任何介面定義語言 (IDL) 設定。  
  
5.  按一下 [完成] 以新增屬性。  
  
 屬性的 **Get** 和 `Put` 方法會顯示為 [類別檢視] 中，其定義所在介面下方的兩個圖示。 您可以按兩下任一個圖示來檢視 .idl 檔案中的屬性宣告。  
  
-   針對 ATL 介面，**Get** 和 **Put** 函式會新增至 .cpp 檔案中，並將這些函式的參考新增至 .h 檔案。  
  
-   針對 MFC 分配介面，如果您選取 [成員變數] 作為實作類型，方法和變數會新增至實作它的類別。 如果您選取 [Get/Set 方法] 作為實作類型，兩種方法會新增至實作它的類別。  
  
## <a name="see-also"></a>請參閱  
 [建立 COM 介面](../ide/creating-a-com-interface-visual-cpp.md)   
 [編輯 COM 介面](../ide/editing-a-com-interface.md)   
 [元件物件模型](/windows/desktop/com/the-component-object-model)   
 [介面指標和介面](/windows/desktop/com/interface-pointers-and-interfaces)