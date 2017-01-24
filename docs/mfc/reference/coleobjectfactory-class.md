---
title: "COleObjectFactory Class | Microsoft Docs"
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
  - "COleObjectFactory"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "class factories, COleObjectFactory class"
  - "COleObjectFactory class"
  - "建立物件, OLE 物件"
  - "物件 [C++], 建立 OLE"
  - "OLE class factory"
  - "OLE 物件"
  - "OLE 物件, 建立"
  - "OLE, class factory"
ms.assetid: ab179c1e-4af2-44aa-a576-37c48149b427
caps.latest.revision: 21
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# COleObjectFactory Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

實作 OLE Class Factory，建立 OLE 物件 \(例如伺服器， Automation 物件，並會記錄。  
  
## 語法  
  
```  
class COleObjectFactory : public CCmdTarget  
```  
  
## 成員  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[COleObjectFactory::COleObjectFactory](../Topic/COleObjectFactory::COleObjectFactory.md)|建構 `COleObjectFactory` 物件。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[COleObjectFactory::GetClassID](../Topic/COleObjectFactory::GetClassID.md)|傳回物件的 OLE 類別 ID Factory 建立。|  
|[COleObjectFactory::IsLicenseValid](../Topic/COleObjectFactory::IsLicenseValid.md)|決定控制項的授權是否有效。|  
|[COleObjectFactory::IsRegistered](../Topic/COleObjectFactory::IsRegistered.md)|指示物件 Factory 向這個 OLE 系統 DLL 註冊。|  
|[COleObjectFactory::Register](../Topic/COleObjectFactory::Register.md)|註冊具有 OLE 系統 DLL 這個 Object Factory。|  
|[COleObjectFactory::RegisterAll](../Topic/COleObjectFactory::RegisterAll.md)|註冊所有具有 OLE 系統 DLL 應用程式物件的 Factory。|  
|[COleObjectFactory::Revoke](../Topic/COleObjectFactory::Revoke.md)|移除與這個 OLE 系統 DLL 的這個 Object Factory 的註冊。|  
|[COleObjectFactory::RevokeAll](../Topic/COleObjectFactory::RevokeAll.md)|移除應用程式的物件具有 OLE 系統 DLL 的 Factory 的註冊。|  
|[COleObjectFactory::UnregisterAll](../Topic/COleObjectFactory::UnregisterAll.md)|應用程式的 Object Factory 的全部移除。|  
|[COleObjectFactory::UpdateRegistry](../Topic/COleObjectFactory::UpdateRegistry.md)|註冊 OLE 系統註冊這個 Object Factory。|  
|[COleObjectFactory::UpdateRegistryAll](../Topic/COleObjectFactory::UpdateRegistryAll.md)|註冊所有具有 OLE 系統註冊的應用程式物件的 Factory。|  
  
### 受保護的方法  
  
|名稱|描述|  
|--------|--------|  
|[COleObjectFactory::GetLicenseKey](../Topic/COleObjectFactory::GetLicenseKey.md)|要求控制項的 DLL 的唯一索引鍵。|  
|[COleObjectFactory::OnCreateObject](../Topic/COleObjectFactory::OnCreateObject.md)|呼叫由架構建立 Factory 型別的新物件。|  
|[COleObjectFactory::VerifyLicenseKey](../Topic/COleObjectFactory::VerifyLicenseKey.md)|驗證在控制項內嵌在的索引鍵符合在容器中的金鑰。|  
|[COleObjectFactory::VerifyUserLicense](../Topic/COleObjectFactory::VerifyUserLicense.md)|驗證控制項允許在設計階段使用。|  
  
## 備註  
 `COleObjectFactory` 類別會執行的下列函式成員函式:  
  
-   處理物件的註冊。  
  
-   更新 OLE 系統暫存器，以及通知 OLE 的執行階段註冊物件循序和準備接收訊息。  
  
-   強制執行允許藉由限制對控制項的用法授權的開發人員在設計階段和為允許應用程式在執行階段。  
  
-   註冊控制項具有 OLE 系統登錄的 Object Factory。  
  
 如需建立物件的詳細資訊，請參閱 Microsoft 知識庫文件 [資料物件和資料來源 \(Object Linking\)](../../mfc/data-objects-and-data-sources-ole.md) 和 [資料物件和資料來源:建立與解構](../../mfc/data-objects-and-data-sources-creation-and-destruction.md)。  如需更多關於登入，請參閱本文 [登入](../../mfc/registration.md)。  
  
## 繼承階層架構  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 `COleObjectFactory`  
  
## 需求  
 **Header:** afxdisp.h  
  
## 請參閱  
 [CCmdTarget Class](../../mfc/reference/ccmdtarget-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [COleTemplateServer Class](../../mfc/reference/coletemplateserver-class.md)