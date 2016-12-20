---
title: "如何：測試相關說明和啟動顯示畫面 | Microsoft Docs"
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
ms.assetid: 2b959fa4-56d3-44f4-8c2d-9ea2e6fb269d
caps.latest.revision: 10
caps.handback.revision: 10
manager: "douge"
---
# 如何：測試相關說明和啟動顯示畫面
實作後**詳見 \[說明**和開頭顯示畫面的支援，您可以測試您的實作，在[!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)]。  
  
### 若要測試 \[說明\] \[關於\] 對話方塊  
  
1.  從[!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)]命令提示字元中執行與 devenv.exe **\/setup**切換。  若要執行在實驗環境中，請鍵入：  
  
     **devenv \/rootsuffix Exp \/setup**  
  
     **附註**您不必重複此步驟，只有當您變更 **詳見 \[說明**畫面的資訊。  
  
2.  執行[!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)]在相同的登錄根目錄為了先前所述，但不使用**\/setup**切換：  
  
     **devenv \/rootsuffix Exp**  
  
3.  在**幫助** \] 功能表中，按一下 **有關 Microsoft Visual Studio**。  
  
     VSPackage 名稱會出現在**已安裝產品**清單。  
  
4.  從清單中選取您的 VSPackage。  
  
     VSPackage 產品資訊會出現在**產品詳細資料** \] 文字方塊。  
  
### 若要測試的啟動顯示畫面  
  
1.  執行與 devenv.exe **\/setup**切換。  若要執行在實驗環境中，請鍵入：  
  
     **devenv \/rootsuffix Exp \/setup**  
  
     **附註**您不必重複此步驟，只有當您變更開頭顯示畫面的資訊時。  
  
2.  執行[!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)]為相同的登錄根目錄中前述更早版本，但是與**\/splash**切換，而不是**\/setup**切換。  
  
     **devenv \/rootsuffix Exp \/splash**  
  
     您的 VSPackage 產品資訊和商標就會出現在開頭顯示畫面上。  
  
## 請參閱  
 [VSPackage 品牌](../misc/vspackage-branding.md)