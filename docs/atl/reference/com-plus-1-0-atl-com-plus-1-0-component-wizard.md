---
title: COM + 1.0，ATL COM + 1.0 元件精靈 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- vc.codewiz.class.atl.mts.options
dev_langs:
- C++
ms.assetid: 2fbe259c-6be1-4d0e-9cfe-721c75c97cb1
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 9a23f148fbdc611c8a11d8116b2e7dff34fc9d8f
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32358201"
---
# <a name="com-10-atl-com-10-component-wizard"></a>COM+ 1.0, ATL COM+ 1.0 元件精靈
若要指定介面類型和其他介面必須支援使用 ATL COM + 1.0 元件精靈的這個頁面。  
  
 如需 ATL 專案和 ATL COM 類別的詳細資訊，請參閱[ATL COM 桌面元件](../../atl/atl-com-desktop-components.md)。  
  
 **Interface**  
 表示物件支援的介面的型別。 根據預設，物件會支援雙重介面。  
  
|選項|描述|  
|------------|-----------------|  
|**雙重**|指定物件是否支援雙重介面 (其 vtable 具有自訂介面函式和晚期繫結`IDispatch`方法)。 可讓 COM 用戶端和 Automation 控制器存取的物件。|  
|**自訂**|指定物件支援自訂介面 （其 vtable 有自訂介面函式）。 自訂介面可以比雙重介面，更快，尤其是跨處理序界限。<br /><br /> -   **Automation 相容**自動化支援加入自訂的介面。 屬性化專案，請設定**oleautomation**在 coclass 的屬性。|  
  
 **Queueable**  
 表示用戶端可以呼叫此元件以非同步方式使用訊息佇列。 .H 檔案 （屬性化專案） 或.idl 檔案 （非屬性化專案），請新增元件的屬性化巨集自訂 (TLBATTR_QUEUEABLE，0)。  
  
 **支援**  
 指出錯誤處理和物件控制的其他支援。  
  
|選項|描述|  
|------------|-----------------|  
|**ISupportErrorInfo**|建立支援[ISupportErrorInfo](../../atl/reference/isupporterrorinfoimpl-class.md)介面讓物件可以將錯誤資訊傳回給用戶端。|  
|**IObjectControl**|提供三個物件存取[IObjectControl](http://msdn.microsoft.com/library/windows/desktop/ms686474)方法： [Activate](http://msdn.microsoft.com/library/windows/desktop/ms681303)， [CanBePooled](http://msdn.microsoft.com/library/windows/desktop/ms684322)，和[停用](http://msdn.microsoft.com/library/windows/desktop/ms687094)。|  
|**IObjectConstruct**|建立支援[IObjectConstruct](http://msdn.microsoft.com/library/windows/desktop/ms680583)介面來傳遞管理來自其他物件或方法參數中。|  
  
 **異動**  
 指出物件支援交易。 包含檔案 mtxattr.h.idl 檔中 （非屬性化專案）。  
  
|選項|描述|  
|------------|-----------------|  
|**支援**|指定物件從未交易資料流的根目錄加元件屬性的巨集 custom(TLBATTR_TRANS_SUPPORTED,0).h 檔案 （屬性化專案） 或.idl 檔案 （非屬性化專案）。|  
|**必要**|指定物件可能，也可能不是藉由新增元件屬性的巨集 custom(TLBATTR_TRANS_REQUIRED,0).h 檔案 （屬性化專案） 或.idl 檔案 （非屬性化專案） 的交易資料流的根目錄。|  
|**不支援**|指定物件排除的交易。 將元件屬性的巨集 custom(TLBATTR_TRANS_NOTSUPP,0) 加入至.h 檔案 （屬性化專案） 或.idl 檔案 （非屬性化專案）。|  
|**需要新增**|指定物件一律交易資料流的根目錄加元件屬性的巨集 custom(TLBATTR_TRANS_REQNEW,0).h 檔案 （屬性化專案） 或.idl 檔案 （非屬性化專案）。|  
  
## <a name="see-also"></a>另請參閱  
 [ATL COM + 1.0 元件精靈](../../atl/reference/atl-com-plus-1-0-component-wizard.md)   
 [ATL COM + 1.0 元件](../../atl/reference/adding-an-atl-com-plus-1-0-component.md)

