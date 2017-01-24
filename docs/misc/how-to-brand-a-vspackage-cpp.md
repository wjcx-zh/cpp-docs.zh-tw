---
title: "如何：設定 VSPackage 的品牌 (C++) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "關於對話方塊"
  - "VSPackage, 啟動顯示畫面"
  - "VSPackage, 品牌"
ms.assetid: a1b9213f-8702-4716-8623-cd3705d531fa
caps.latest.revision: 10
caps.handback.revision: 10
manager: "douge"
---
# 如何：設定 VSPackage 的品牌 (C++)
若要顯示在**詳見 \[說明**對話方塊並啟動顯示畫面，就必須實作 VSPackages <xref:Microsoft.VisualStudio.Shell.Interop.IVsInstalledProduct>介面。  此舉可以提供下列資訊，以[!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)]：  
  
-   名稱  
  
-   識別碼，如序列連接埠或版本號碼  
  
-   資訊  
  
-   標誌的圖示  
  
 `IVsInstalledProductImpl`類別會取得該資訊的樣板參數。  每個範本參數是 id。  前三個字串資源識別碼，第四個是一個圖示資源 ID。  
  
## 範例  
 下列類別宣告為 VSPackage 類別是從[VSSDK 範例](../misc/vssdk-samples.md)。  
  
```  
class ATL_NO_VTABLE BasicPackage :   
  ...  
  public IVsInstalledProductImpl<  
    IDS_BASICPACKAGE_PRODUCT_NAME,  
    IDS_BASICPACKAGE_PRODUCT_IDENTIFIER,   
    IDS_BASICPACKAGE_PRODUCT_DETAILS,   
    IDI_BASICPACKAGE_LOGO>  
```  
  
 若要測試您的 VSPackage，請參閱[如何：測試相關說明和啟動顯示畫面](../misc/how-to-test-the-help-about-and-splash-screens.md)。  
  
## 請參閱  
 [VSPackage 品牌](../misc/vspackage-branding.md)