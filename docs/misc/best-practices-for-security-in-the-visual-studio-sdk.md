---
title: "Visual Studio SDK 中的安全性最佳做法 | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "安全性 [Visual Studio SDK]"
  - "使用者帳戶控制 [Visual Studio SDK]"
  - "Visual Studio SDK, 安全性"
  - "UAC (使用者帳戶控制) [Visual Studio SDK]"
  - "安全性最佳做法, Visual Studio SDK"
  - "Windows Vista, 使用者帳戶控制 [Visual Studio SDK]"
ms.assetid: 56c8a113-0c53-4969-a009-a2ab58d855c3
caps.latest.revision: 30
caps.handback.revision: 30
manager: "douge"
---
# Visual Studio SDK 中的安全性最佳做法
您需要了解 VSPackage 擴充功能的安全性，以便建立可能的最佳產品。  
  
 安全的產品可協助保護下列各項：  
  
-   客戶資訊的機密性、完整性和可用性。  
  
-   系統擁有者或系統管理員控制下之處理資源的完整性和可用性。  
  
## 安全性弱點  
 安全性弱點是產品中的弱點，導致無法防止攻擊者的惡意活動，即使產品使用正確時亦然。 以下是一些範例：  
  
-   在電腦上取得高於使用者的權限。  
  
-   接管使用者電腦的作業。  
  
-   洩露使用者電腦上的資料。  
  
> [!IMPORTANT]
>  絕對不要假設您的應用程式只會在特定環境中執行。 您的應用程式可能會使用在您未預期的設定中，尤其是當應用程式變得熱門時。 假設您的程式碼改為在不安全的環境中執行和設計、撰寫，並據以測試您的程式碼。  
  
 以安全性為主要功能來設計及建置產品和系統，會比事後補強安全性的產品和系統更穩固。 安全的產品也更能免於媒體批評、更能吸引使用者，支援和升級也比較便宜。  
  
## 危險的 API  
 呼叫某些函式時，如果它們的用法不正確，可能會產生不必要的安全性弱點，但禁用它們卻不一定會產生安全的程式碼。 不過，有些軟體專案藉由禁用難以安全使用的函式，而明顯提升安全性，這是許多安全開發做法的其中一種。 如需詳細資訊，請參閱 Microsoft Press 書籍《撰寫安全程式碼》的附錄 A，本書由 Michael Howard 與 David LeBlanc 所著。  
  
 大部分的安全性問題起因於信任輸入，而未充分進行確認。 請確定您在資料進入程式碼時加以追蹤，並且質疑對該資料的作業的影響。 您可以使用大部分函式來撰寫安全程式碼，如果資料輸入格式正確且已檢查可信度。  
  
## 使用者帳戶控制 \(UAC\) 問題  
 使用者帳戶控制 \(UAC\) 功能具有您應該了解的安全性影響。 它減少了作業系統與應用程式曝露在惡意攻擊中的風險。  
  
1.  如需 [!INCLUDE[win7](../build/includes/win7_md.md)] 上 UAC 的詳細資訊，請參閱[什麼是使用者帳戶控制？](http://go.microsoft.com/fwlink/?linkid=159927)。  
  
2.  如需 [!INCLUDE[win8](../build/includes/win8_md.md)] 上 UAC 的詳細資訊，請參閱[什麼是使用者帳戶控制設定？](http://windows.microsoft.com/windows-8/what-are-uac-settings)。  
  
 UAC 問世之前，開發人員通常使用系統管理員權限來執行 [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)]，即使是不必要的時候。 您應該以一般使用者的身分執行擴充功能的開發和測試，因此您可以確定它不會不必要地提高權限。  
  
 請注意，UAC 也會影響部署。 必須正確地撰寫安裝封裝，以支援 UAC。 撰寫不正確的封裝通常會導致「拒絕存取」錯誤，因為安裝程式會嘗試使用一般使用者權限來執行需要提高權限的工作。  
  
## 請參閱  
 [在 Vspackage 中的安全性最佳作法](../Topic/Best%20Practices%20for%20Security%20in%20VSPackages.md)   
 [建立安全應用程式的資源](http://msdn.microsoft.com/zh-tw/0ebf5f69-76f2-498a-a2df-83cf3443e132)   
 [Key Security Concepts](../Topic/Key%20Security%20Concepts.md)