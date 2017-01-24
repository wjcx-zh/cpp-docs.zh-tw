---
title: "將使用者控制項置於工具視窗 | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "工具視窗, 加入使用者控制項"
  - "使用者控制項 [Visual Studio SDK], 加入工具視窗中"
  - "使用者控制項 [Visual Studio SDK]"
ms.assetid: 869f3195-e152-4e61-802c-51d6b7ba3e36
caps.latest.revision: 29
caps.handback.revision: 29
manager: "douge"
---
# 將使用者控制項置於工具視窗
本逐步解說示範如何將使用者控制項加入工具視窗中。  
  
 使用者控制項是指繫結為一個控制項的 Windows 控制項集合。 若要將使用者控制項加入工具視窗中，您只需要在 \[工具箱\] 中顯示使用者控制項。 本逐步解說所使用的使用者控制項是在[逐步解說：使用 Visual C\# 撰寫複合控制項](../Topic/Walkthrough:%20Authoring%20a%20Composite%20Control%20with%20Visual%20C%23.md)中開發的時鐘控制項。  
  
## 必要條件  
 若要依照本逐步解說執行作業，您必須安裝 Visual Studio SDK。 如需詳細資訊，請參閱[Visual Studio SDK](../Topic/Visual%20Studio%20SDK.md)。  
  
## 建立使用者控制項  
  
1.  依照[逐步解說：使用 Visual C\# 撰寫複合控制項](../Topic/Walkthrough:%20Authoring%20a%20Composite%20Control%20with%20Visual%20C%23.md)中的步驟執行，以建立時鐘控制項。 請勿建立鬧鐘控制項。  
  
> [!NOTE]
>  下列步驟假設您將時鐘控制項命名為 `ctlClock`。  
  
## 建立工具視窗擴充功能  
  
1.  建立名為 `MyToolWindowPackageUC` 的 VSIX 專案，其中包含名為 `MyToolWindow` 的工具視窗。 如果您需要協助來執行這項作業，請參閱[建立擴充功能與工具視窗](../Topic/Creating%20an%20Extension%20with%20a%20Tool%20Window.md)。  
  
## 加入使用者控制項  
  
1.  在**方案總管**中，以滑鼠右鍵按一下方案 **MyToolWindowPackageUC**，指向 \[加入\]，然後按一下 \[現有專案\]。  
  
2.  在 \[加入現有專案\] 對話方塊中，開啟 ctlClockLib 專案並選取 ctlClock.lib.csproj 專案檔。 按一下 \[**確定**\]。 這會啟用可在設計工具中使用的使用者控制項。  
  
3.  在**方案總管**中，以滑鼠右鍵按一下 MyToolWindowControl.cs，然後選取 \[設計工具檢視\]。 這會開啟表單設計工具，其中顯示為工具視窗所產生的控制項。  
  
4.  開啟 \[工具箱\]，找出標示為 \[ctlClockLib 元件\] 的區段，然後按兩下該區段中的 **ctlClock** 控制項，將控制項加入表單中。 只要隱藏 \[工具箱\]，就能在您的工具視窗表單中看到時間顯示。  
  
5.  在設計工具中，選取剛才加入的時鐘控制項，然後將 **Anchor** 屬性變更為 \[靠上\]。  
  
6.  在**方案總管**中，以滑鼠右鍵按一下 ctlClockLib 專案節點，然後按一下 \[屬性\]。  
  
7.  在 \[簽署\] 索引標籤上，選取 \[簽署組件\]。 在 \[選擇強式名稱金鑰檔\] 方塊中，按一下 \[\<瀏覽\>\]，然後巡覽至 **MyToolWindowPackageUC** 專案資料夾中的 key.snk 檔案。  
  
8.  編譯程式，並確定沒有任何錯誤。 這個步驟使用 Visual Studio 註冊 VSPackage 及其工具視窗。  
  
9. 按 F5 鍵在實驗登錄區中開啟 Visual Studio 的執行個體。  
  
10. 在實驗性 Visual Studio 的 \[檢視\] 功能表中，指向 \[其他視窗\]，然後按一下 \[MyToolWindow\]。 這會顯示具有執行時間顯示的工具視窗。  
  
## 請參閱  
 [逐步解說：使用 Visual C\# 撰寫複合控制項](../Topic/Walkthrough:%20Authoring%20a%20Composite%20Control%20with%20Visual%20C%23.md)