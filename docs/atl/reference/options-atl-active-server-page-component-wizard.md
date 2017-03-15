---
title: "選項、 ATL 動態伺服器網頁元件精靈 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- vc.codewiz.class.atl.asp.options
dev_langs:
- C++
helpviewer_keywords:
- ATL Active Server Page Component Wizard, options
ms.assetid: 54f34e26-53c7-4456-9675-cb86e356bde0
caps.latest.revision: 12
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 3168772cbb7e8127523bc2fc2da5cc9b4f59beb8
ms.openlocfilehash: 608b7747c70286ed3bf9598036ac672881730815
ms.lasthandoff: 02/24/2017

---
# <a name="options-atl-active-server-page-component-wizard"></a>選項, ATL Active Server Page 元件精靈
您可以使用 ATL Active Server 網頁元件精靈的這個頁面來設計以提升的效率及錯誤支援物件。  
  
 如需 ATL 專案和 ATL COM 類別的詳細資訊，請參閱[ATL COM 桌面元件](../../atl/atl-com-desktop-components.md)。  
  
 **執行緒模型**  
 表示管理執行緒的方法。 根據預設，專案會使用**Apartment**執行緒。  
  
 請參閱[指定專案的執行緒模型](../../atl/specifying-the-threading-model-for-a-project-atl.md)如需詳細資訊。  
  
|選項|說明|  
|------------|-----------------|  
|`Single`|指定的物件會使用單一執行緒模型。 在單一執行緒模型中，物件一定是在主要 COM 執行緒。 請參閱[單一執行緒 Apartment](http://msdn.microsoft.com/library/windows/desktop/ms680112)和[InprocServer32](http://msdn.microsoft.com/library/windows/desktop/ms682390)如需詳細資訊。|  
|**Apartment**|指定物件使用 apartment 執行緒。 相當於單一執行緒 apartment 中。 Apartment 執行緒元件的每個物件會指派 apartment 其執行緒，物件的存留期不過，多個執行緒可以使用多個物件。 每個 apartment 繫結至特定的執行緒，而且 Windows 訊息幫浦 （預設值）。<br /><br /> 請參閱[單一執行緒 Apartment](http://msdn.microsoft.com/library/windows/desktop/ms680112)如需詳細資訊。|  
|**兩者**|指定的物件可以使用 apartment 或無限制執行緒，取決於哪一種執行緒建立。|  
|**免費**|指定物件使用無限制執行緒。 無限制執行緒相當於多執行緒 apartment 模型。 請參閱[多執行緒 Apartment](http://msdn.microsoft.com/library/windows/desktop/ms693421)如需詳細資訊。|  
|**中性**(僅限 Windows 2000)|指定物件會遵循多執行緒 apartment 的指導方針，但它可以在任何種類的執行緒上執行。|  
  
 **彙總**  
 指出物件是否使用[彙總](http://msdn.microsoft.com/library/windows/desktop/ms686558)。 彙總物件可讓您選擇的介面來公開給用戶端，並介面會公開一樣加以彙總物件實作。 彙總物件的用戶端通訊只能搭配彙總的物件。  
  
|選項|說明|  
|------------|-----------------|  
|**[是]**|指定物件可以彙總。 預設值。|  
|**No**|指定的物件不會彙總。|  
|**只有**|指定物件必須彙總。|  
  
 **支援**  
 （要新增的項目描述）  
  
|選項|說明|  
|------------|-----------------|  
|**ISupportErrorInfo**|建立支援[ISupportErrorInfo](../../atl/reference/isupporterrorinfoimpl-class.md)介面讓物件可以將錯誤資訊傳回給用戶端。|  
|**連接點**|藉由衍生自物件的類別可讓您物件的連接點[IConnectionPointContainerImpl](../../atl/reference/iconnectionpointcontainerimpl-class.md)。|  
|**無限制執行緒封送處理器**|建立無限制執行緒封送處理器物件來有效率地在相同的程序中執行緒之間封送處理介面指標。 指定的物件可供**兩者**或**免費**為執行緒模型。|  
  
## <a name="see-also"></a>另請參閱  
 [ATL 動態伺服器網頁元件精靈](../../atl/reference/atl-active-server-page-component-wizard.md)   
 [ATL 動態伺服器網頁元件](../../atl/reference/adding-an-atl-active-server-page-component.md)


