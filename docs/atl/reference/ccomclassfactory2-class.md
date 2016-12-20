---
title: "CComClassFactory2 Class | Microsoft Docs"
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
  - "ATL::CComClassFactory2<license>"
  - "CComClassFactory2"
  - "ATL.CComClassFactory2<license>"
  - "ATL::CComClassFactory2"
  - "ATL.CComClassFactory2"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CComClassFactory2 class"
ms.assetid: 19b66fd6-b9ed-47a0-822c-8132184f5a3e
caps.latest.revision: 20
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CComClassFactory2 Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

這個類別會實作介面 [IClassFactory2](http://msdn.microsoft.com/library/windows/desktop/ms692720) 。  
  
## 語法  
  
```  
  
      template <  
   class license  
>  
class CComClassFactory2 : public IClassFactory2,  
   public CComObjectRootEx<CComGlobalsThreadModel>,  
   public license  
```  
  
#### 參數  
 *授權*  
 實作下列靜態函式的類別:  
  
-   **static BOOL VerifyLicenseKey\( BSTR**  `bstr`\);  
  
-   **static BOOL GetLicenseKey\( DWORD**  `dwReserved` **, BSTR\***  `pBstr`\);  
  
-   **static BOOL IsLicenseValid\( \);**  
  
## Members  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CComClassFactory2::CreateInstance](../Topic/CComClassFactory2::CreateInstance.md)|建立指定的 CLSID 的物件。|  
|[CComClassFactory2::CreateInstanceLic](../Topic/CComClassFactory2::CreateInstanceLic.md)|將授權金鑰，建立指定的 CLSID 的物件。|  
|[CComClassFactory2::GetLicInfo](../Topic/CComClassFactory2::GetLicInfo.md)|擷取描述 Class Factory 授權功能的相關資訊。|  
|[CComClassFactory2::LockServer](../Topic/CComClassFactory2::LockServer.md)|鎖定在記憶體的 Class Factory。|  
|[CComClassFactory2::RequestLicKey](../Topic/CComClassFactory2::RequestLicKey.md)|授權金鑰建立和傳回。|  
  
## 備註  
 `CComClassFactory2` [IClassFactory2](http://msdn.microsoft.com/library/windows/desktop/ms692720) 實作介面，則為 [IClassFactory](http://msdn.microsoft.com/library/windows/desktop/ms694364)副檔名。  **IClassFactory2** 控制項透過授權物件建立。  執行授權的電腦的 Class Factory 可以提供執行階段授權識別碼。  當完整授權的電腦能夠不存在時，這個授權識別碼可讓應用程式執行個體化物件。  
  
 ATL 物件以下列方式通常是安全的 Class Factory。 [CComCoClass](../../atl/reference/ccomcoclass-class.md)。  這個類別包含巨集 [DECLARE\_CLASSFACTORY](../Topic/DECLARE_CLASSFACTORY.md)，宣告 [CComClassFactory](../../atl/reference/ccomclassfactory-class.md) 做為預設的 Class Factory。  若要使用 `CComClassFactory2`，請指定 [DECLARE\_ CLASSFACTORY2](../Topic/DECLARE_CLASSFACTORY2.md) 巨集在物件的類別定義。  例如：  
  
 [!code-cpp[NVC_ATL_COM#2](../../atl/codesnippet/CPP/ccomclassfactory2-class_1.h)]  
  
 **CMyLicense**，對 `CComClassFactory2`的樣板參數時，必須實作靜態函式 `VerifyLicenseKey`、 `GetLicenseKey`和 `IsLicenseValid`。  以下是簡單的授權的類別範例:  
  
 [!code-cpp[NVC_ATL_COM#3](../../atl/codesnippet/CPP/ccomclassfactory2-class_2.h)]  
  
 `CComClassFactory2` 從 **CComClassFactory2Base** 和 *授權*衍生。  **CComClassFactory2Base**，接著，從 **IClassFactory2** 和 **CComObjectRootEx\< CComGlobalsThreadModel \>**衍生。  
  
## 繼承階層架構  
 `CComObjectRootBase`  
  
 `license`  
  
 [CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)  
  
 `IClassFactory2`  
  
 `CComClassFactory2`  
  
## 需求  
 **Header:** atlcom.h  
  
## 請參閱  
 [CComClassFactoryAutoThread Class](../../atl/reference/ccomclassfactoryautothread-class.md)   
 [CComClassFactorySingleton Class](../../atl/reference/ccomclassfactorysingleton-class.md)   
 [CComObjectRootEx Class](../../atl/reference/ccomobjectrootex-class.md)   
 [CComGlobalsThreadModel](../Topic/CComGlobalsThreadModel.md)   
 [Class Overview](../../atl/atl-class-overview.md)