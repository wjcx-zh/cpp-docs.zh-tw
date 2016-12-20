---
title: "COM+ 1.0, ATL COM+ 1.0 元件精靈 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "vc.codewiz.class.atl.mts.options"
dev_langs: 
  - "C++"
ms.assetid: 2fbe259c-6be1-4d0e-9cfe-721c75c97cb1
caps.latest.revision: 11
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# COM+ 1.0, ATL COM+ 1.0 元件精靈
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

您可使用此 ATL COM\+ 1.0 元件精靈頁面來指定要支援的介面類型和其他介面。  
  
 如需 ATL 專案和 ATL COM 類別的詳細資訊，請參閱 [ATL COM Desktop Components](../../atl/atl-com-desktop-components.md)。  
  
 **介面**  
 指示物件支援的介面類型。  物件預設支援雙重介面。  
  
|選項|描述|  
|--------|--------|  
|**雙重**|指定物件支援雙重介面 \(其 vtable 具有自訂介面函式和晚期繫結 \(Late Binding\) `IDispatch` 方法\)。  允許 COM 用戶端和 Automation 控制程式存取物件。|  
|**Custom**|指定物件支援自訂介面 \(其 vtable 具有自訂介面函式\)。  自訂介面比雙重介面的速度快，特別是在跨處理序 \(Process\) 界限的時候。<br /><br /> -   **Automation compatible** 加入 Automation 支援加入至介面。  屬性化專案則是設定 coclass 中的 **oleautomation** 屬性。|  
  
 **可排入佇列**  
 指示用戶端可使用訊息佇列來非同步呼叫這個元件。  將元件屬性化巨集 custom\(TLBATTR\_QUEUEABLE, 0\) 加入至 .h 檔案 \(屬性化專案\) 或 .idl 檔案 \(非屬性化專案\)。  
  
 **支援**  
 指定錯誤處理和物件控制項的其他支援。  
  
|選項|描述|  
|--------|--------|  
|**ISupportErrorInfo**|建立 [ISupportErrorInfo](../../atl/reference/isupporterrorinfoimpl-class.md) 介面的支援，使物件能夠將錯誤資訊傳回用戶端。|  
|**IObjectControl**|將物件存取提供給三個 [IObjectControl](http://msdn.microsoft.com/library/windows/desktop/ms686474) 方法：[Activate](http://msdn.microsoft.com/library/windows/desktop/ms681303)、[CanBePooled](http://msdn.microsoft.com/library/windows/desktop/ms684322) 和 [Deactivate](http://msdn.microsoft.com/library/windows/desktop/ms687094)。|  
|**IObjectConstruct**|建立 [IObjectConstruct](http://msdn.microsoft.com/library/windows/desktop/ms680583) 介面的支援來管理從其他方法或物件傳入的參數。|  
  
 **異動**  
 指示物件支援交易。  將 mtxattr.h 檔案包含在 .idl 檔案 \(非屬性化專案\) 中。  
  
|選項|描述|  
|--------|--------|  
|**支援項目**|指定物件不會成為交易資料流的根 \(Root\)，方式是將元件屬性巨集 custom\(TLBATTR\_TRANS\_SUPPORTED, 0\) 加入至 .h 檔案 \(屬性化專案\) 或 .idl 檔案 \(非屬性化專案\)。|  
|**必要項**|指定物件可以或不可以成為交易資料流的根，方式是將元件屬性巨集 custom\(TLBATTR\_TRANS\_REQUIRED, 0\) 加入至 .h 檔案 \(屬性化專案\) 或 .idl 檔案 \(非屬性化專案\)。|  
|**不支援**|指定物件排除交易。  將元件屬性巨集自訂 \(TLBATTR\_TRANS\_NOTSUPP、0\) 加入至 .h 檔案 \(屬性化專案\) 或 .idl 檔案 \(非屬性化專案\)。|  
|**必須是新交易**|指定物件都是交易資料流的根，方式是將元件屬性巨集 custom\(TLBATTR\_TRANS\_REQNEW, 0\) 加入至 .h 檔案 \(屬性化專案\) 或 .idl 檔案 \(非屬性化專案\)。|  
  
## 請參閱  
 [ATL COM\+ 1.0 元件精靈](../../atl/reference/atl-com-plus-1-0-component-wizard.md)   
 [ATL COM\+ 1.0 Component](../../atl/reference/adding-an-atl-com-plus-1-0-component.md)