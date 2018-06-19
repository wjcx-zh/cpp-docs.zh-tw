---
title: 視覺化管理員 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- Visualization Manager
ms.assetid: c9dd1365-27ac-42e5-8caa-1004525b4129
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 40d16e1373d347b4a715cd6f073211796913bd21
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33384211"
---
# <a name="visualization-manager"></a>視覺化管理員
視覺化管理員是控制整個應用程式的外觀的物件。 其會成為單一類別您可以在其中放置您的應用程式的所有繪圖程式碼。 MFC 程式庫包含數個視覺管理員。 如果您想要建立您的應用程式的自訂檢視，您也可以建立您自己的視覺管理員。 下列影像顯示相同的應用程式，啟用不同的視覺管理員時：  
  
 ![由 CMFCVisualManagerWindows 呈現的 MyApp](../mfc/media/vmwindows.png "vmwindows")  
使用 CMFCVisualManagerWindows 視覺化管理員的 MyApp  
  
 ![由 CMFCVisualManagerVS2005 呈現的 MyApp](../mfc/media/vmvs2005.png "vmvs2005")  
使用 CMFCVisualManagerVS2005 視覺化管理員的 MyApp  
  
 ![由 CMFCVisualManagerOfficeXP 呈現的 MyApp](../mfc/media/vmofficexp.png "vmofficexp")  
使用 CMFCVisualManagerOfficeXP 視覺化管理員的 MyApp  
  
 ![由 CMFCVisualManagerOffice2003 呈現的 MyApp](../mfc/media/vmoffice2003.png "vmoffice2003")  
使用 CMFCVisualManagerOffice2003 視覺化管理員的 MyApp  
  
 ![由 CMFCVisualManagerOffice2007 呈現的 MyApp](../mfc/media/msoffice2007.png "msoffice2007")  
使用 CMFCVisualManagerOffice2007 視覺化管理員的 MyApp  
  
 依預設，視覺管理員會維持數個的 GUI 項目的繪圖程式碼。 若要提供自訂 UI 項目，您需要覆寫的視覺管理員相關的繪圖方法。 如需這些方法的清單，請參閱[CMFCVisualManager 類別](../mfc/reference/cmfcvisualmanager-class.md)。 您可以覆寫，以提供自訂的外觀的方法為開頭的所有方法`OnDraw`。  
  
 您的應用程式只能有一個`CMFCVisualManager`物件。 若要取得您的應用程式的視覺化管理員的指標，呼叫靜態函式[CMFCVisualManager::GetInstance](../mfc/reference/cmfcvisualmanager-class.md#getinstance)。 因為所有的視覺管理員是繼承自`CMFCVisualManager`、`CMFCVisualManager::GetInstance`方法會取得的指標適當的視覺管理員，即使您建立自訂的視覺管理員。  
  
 如果您想要建立自訂的視覺管理員，必須先將它衍生自的視覺管理員已經存在。 若要從衍生的預設類別是`CMFCVisualManager`。 不過，您可以使用不同的視覺管理員，如果它更類似於您要為您的應用程式。 例如，如果您想要使用`CMFCVisualManagerOffice2007`視覺管理員，但想僅適用於變更分隔符號的外觀，您無法衍生自訂類別從`CMFCVisualManagerOffice2007`。 在此案例中，您應該覆寫的方法來繪製分隔符號。  
  
 有兩種應用程式使用特定的視覺化管理員的可能方式。 一種方式是呼叫[CMFCVisualManager::SetDefaultManager](../mfc/reference/cmfcvisualmanager-class.md#setdefaultmanager)方法並傳遞適當的視覺化管理員做為參數。 下列程式碼範例示範如何使用`CMFCVisualManagerVS2005`視覺管理員，使用此方法：  
  
```  
CMFCVisualManager::SetDefaultManager (RUNTIME_CLASS (CMFCVisualManagerVS2005));
```  
  
 其他應用程式中使用視覺化管理員是以手動方式建立它。 應用程式就會將這個新的視覺管理員，用於所有轉譯。 不過，由於可能只有一個`CMFCVisualManager`每個應用程式，您必須先刪除目前的視覺管理員，才能建立一個新物件。 在下列範例中，`CMyVisualManager`是衍生自的自訂視覺化管理員`CMFCVisualManager`。 下列方法將會變更何種視覺管理員用來顯示您的應用程式，根據索引：  
  
```  
void CMyApp::SetSkin (int index)  
{  
    if (CMFCVisualManager::GetInstance() != NULL)  
 {  
    delete CMFCVisualManager::GetInstance();

 }  
 
    switch (index)  
 {  
    case DEFAULT_STYLE: *// The following statement creates a new CMFCVisualManager  
    CMFCVisualManager::GetInstance();
break;  
 
    case CUSTOM_STYLE:  
    new CMyVisualManager;  
    break; 
 
    default: 
    CMFCVisualManager::GetInstance();
break;  
 }  
 
    CMFCVisualManager::GetInstance()->RedrawAll();

} 
```  
  
## <a name="see-also"></a>另請參閱  
 [使用者介面項目](../mfc/user-interface-elements-mfc.md)   
 [CMFCVisualManager 類別](../mfc/reference/cmfcvisualmanager-class.md)
