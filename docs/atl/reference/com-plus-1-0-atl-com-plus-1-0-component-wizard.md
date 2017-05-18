---
title: "COM + 1.0，ATL COM + 1.0 元件精靈 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- vc.codewiz.class.atl.mts.options
dev_langs:
- C++
ms.assetid: 2fbe259c-6be1-4d0e-9cfe-721c75c97cb1
caps.latest.revision: 11
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 3168772cbb7e8127523bc2fc2da5cc9b4f59beb8
ms.openlocfilehash: 36295e5ce296ea6ba982c4ce8cf729bf45860883
ms.contentlocale: zh-tw
ms.lasthandoff: 02/24/2017

---
# <a name="com-10-atl-com-10-component-wizard"></a>COM+ 1.0, ATL COM+ 1.0 元件精靈
使用 ATL COM + 1.0 元件精靈的這個頁面，指定要支援的介面型別和其他介面。  
  
 如需 ATL 專案和 ATL COM 類別的詳細資訊，請參閱[ATL COM 桌面元件](../../atl/atl-com-desktop-components.md)。  
  
 **介面**  
 表示物件支援的介面的型別。 根據預設，物件會支援雙重介面。  
  
|選項|描述|  
|------------|-----------------|  
|**雙重**|指定物件是否支援雙重介面 (其 vtable 具有自訂介面函式和晚期繫結`IDispatch`方法)。 可讓 COM 用戶端和 Automation 控制器存取的物件。|  
|**自訂**|指定物件支援自訂介面 （其 vtable 具有自訂介面函式）。 自訂介面可以較快，雙重介面，尤其是跨處理序界限。<br /><br /> -   **Automation 相容**自動化支援加入自訂的介面。 屬性化專案中，設定**oleautomation**中 coclass 屬性。|  
  
 **Queueable**  
 表示用戶端可以呼叫此元件以非同步方式使用訊息佇列。 .H 檔案 （屬性化專案） 或.idl 檔案 （非屬性化專案），請加入元件屬性的巨集自訂 (TLBATTR_QUEUEABLE，0)。  
  
 **支援**  
 表示錯誤處理和物件控制的其他支援。  
  
|選項|說明|  
|------------|-----------------|  
|**ISupportErrorInfo**|建立支援[ISupportErrorInfo](../../atl/reference/isupporterrorinfoimpl-class.md)介面讓物件可以將錯誤資訊傳回給用戶端。|  
|**IObjectControl**|提供三種您物件的存取[IObjectControl](http://msdn.microsoft.com/library/windows/desktop/ms686474)方法︰[啟動](http://msdn.microsoft.com/library/windows/desktop/ms681303)， [CanBePooled](http://msdn.microsoft.com/library/windows/desktop/ms684322)，和[停用](http://msdn.microsoft.com/library/windows/desktop/ms687094)。|  
|**IObjectConstruct**|建立支援[IObjectConstruct](http://msdn.microsoft.com/library/windows/desktop/ms680583)介面來傳遞管理的其他物件或方法參數。|  
  
 **交易**  
 指出物件支援交易。 包含檔案 mtxattr.h.idl 檔案 （非屬性化專案） 中。  
  
|選項|說明|  
|------------|-----------------|  
|**支援**|指定物件永遠不會交易資料流的根目錄加入元件屬性的巨集 custom(TLBATTR_TRANS_SUPPORTED,0).h 檔案 （屬性化專案） 或.idl 檔案 （非屬性化專案）。|  
|**必要**|指定的物件可能會或可能不是藉由新增元件屬性的巨集 custom(TLBATTR_TRANS_REQUIRED,0).h 檔案 （屬性化專案） 或.idl 檔案 （非屬性化專案） 的交易資料流的根目錄。|  
|**不支援**|指定物件排除交易。 .H 檔案 （屬性化專案） 或.idl 檔案 （非屬性化專案），請加入元件屬性的巨集 custom(TLBATTR_TRANS_NOTSUPP,0)。|  
|**必須是新交易**|指定物件一律交易資料流的根目錄加入元件屬性的巨集 custom(TLBATTR_TRANS_REQNEW,0).h 檔案 （屬性化專案） 或.idl 檔案 （非屬性化專案）。|  
  
## <a name="see-also"></a>另請參閱  
 [ATL COM + 1.0 元件精靈](../../atl/reference/atl-com-plus-1-0-component-wizard.md)   
 [ATL COM + 1.0 元件](../../atl/reference/adding-an-atl-com-plus-1-0-component.md)


