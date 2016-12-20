---
title: "虛擬記憶體不足 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: aec803b1-9d76-46bb-8f14-8c63d80112a5
caps.latest.revision: 13
caps.handback.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# 虛擬記憶體不足
當 虛擬記憶體不足和 [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] 停止回應，就會出現這個訊息。  不過，這個錯誤不是發生在您電腦上的虛擬記憶體不足，而是當 [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] 耗盡位址空間時。  這個錯誤最常發生在運行的 32 位元作業系統的電腦上，這類作業系統限制 [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] 只能有 2GB 的位址空間。  當您以 32 位元處理序時，應用程式只能處理 4 GB 記憶體 \(2^32 位元\)。  不過， Windows 32 位元版本為內部用途保留處理序的虛擬位址空間的 2 GB \(例如，用於與電腦的圖形卡或其他系統驅動程式一起使用\)。  因此， 32 位元處理序只能為其內部用途 2 GB。  使用者可以將 \/3GB 參數保證視窗為本身只保留 1 GB 和 3 GB 的處理序。  在大部分情況下，效能就會降低與 Windows 1 GB 的限制。  
  
 在執行 Windows 64 位元版本的系統時，就會發生這個錯誤，因為處理序會使用所有 4 GB 可定址的空間和視窗，且使用 64 位元記憶體位址與硬體和系統驅動程式一起使用。  不過，當 [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] 處理某些資料集時，記憶體將可能超過 3 GB 和 4 GB。  如[需詳細資訊，請參閱 Visual Studio:為什麼沒有 64 位元版本?\(還有\)](http://go.microsoft.com/fwlink/?LinkId=246307)。  
  
 這個錯誤通常發生在 [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] 快取大量資料，或是執行多個大量耗用記憶體的處理序。  
  
 下列案例牽涉到快取大量資料，通常您可以重新啟動 [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)]修正。  
  
-   第一次安裝之後執行 [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)]。  
  
-   安裝或解除安裝擴充功能。  
  
-   選擇或自訂 **工具箱** 項目。  
  
-   選擇您的[!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)]設定。  
  
-   允許系統在 [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] 開啟的情況下進入睡眠 \(休眠\) 模式。  
  
 以下是需要大量使用中記憶體的案例。  在這些情況下，建議您只開啟主要的元件或只執行其他處理序的 [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] 或在第二個 [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] 執行個體。  
  
-   建置大型方案。  
  
-   使用大型 XML 文件搭配使用。  
  
-   升級方案從 [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)]舊版本。  
  
-   重定方案的目標。  
  
-   在編輯程式碼時執行 [!INCLUDE[esprtfc](../misc/includes/esprtfc_md.md)] 。  
  
-   對多個專案執行 IntelliTrace。  
  
 如果這些測量不發生錯誤，您可以加入在執行 [!INCLUDE[win7](../build/includes/win7_md.md)] 的系統中可用的位址空間，如果您正在跑 bcedit.exe 出現下列文字:  
  
 **bcdedit \/set IncreaseUserVa 3072**  
  
 這個指令可將 x86 系統上 2 GB 的使用者模式虛擬記憶體資源配置增加2 GB 至 3 GB。  如果您加入 \/3GB 參數，整個系統可以處理更多記憶體和給每個應用程式可用記憶體的較大的百分比。  
  
> [!NOTE]
>  您必須以系統管理權限執行 bcdedit.exe。  如果BitLocker 加密已啟用 ，您必須先暫停 Bitlocker，然後進行變更，重新啟動系統，再重新啟用 Bitlocker。  
  
 在您加入到 3 GB 之後的虛擬記憶體的記憶體配置，這項錯誤可能會重複發生，因為單一應用程式只能仍然使用 2 GB 的虛擬記憶體。  如果這項錯誤持續發生，請減少方案的大小，然後重新啟動 [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)]。  您可以減少您的方案任一重構藉由解除安裝不需要專案中或移除不常使用的專案。  當您建置方案時，如果發生錯誤，請嘗試建立它在命令提示字元。  
  
## 請參閱  
 [Resources for Troubleshooting IDE Errors](../Topic/Resources%20for%20Troubleshooting%20Integrated%20Development%20Environment%20Errors.md)