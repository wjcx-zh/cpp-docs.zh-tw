---
title: "How to: Copy Resources | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.resvw.resource.copying"
  - "vs.resvw.resource.copying"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "resources [Visual Studio], moving between files"
  - "resources [Visual Studio], copying"
  - "resource files, copying or moving resources between"
  - "resource files, tiling"
  - ".rc files, copying resources between"
  - "rc files, copying resources between"
ms.assetid: 65f523e8-017f-4fc6-82d1-083c56d9131f
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# How to: Copy Resources
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

您可以在不變更資源的情況下，將資源從一個檔案複製到另一個檔案，也可以[在複製資源時變更其語言和條件](../windows/how-to-change-the-language-or-condition-of-a-resource-while-copying.md)。  
  
 您可以輕易地將資源從現有資源檔或可執行檔複製到您目前的資源檔。  若要執行這項作業，請同時開啟這兩個包含資源的檔案，然後將一個檔案的項目拖曳到另一個檔案，或是在兩個檔案之間進行複製和貼上。  這個方法適用於資源指令碼 \(.rc\) 檔和資源範本 \(.rct\) 檔，以及可執行 \(.exe\) 檔。  
  
> [!NOTE]
>  Visual C\+\+ 包含可供您用於應用程式的範例資源檔。  如需詳細資訊，請參閱 [CLIPART：通用資源](http://msdn.microsoft.com/zh-tw/9bac2891-b6b3-49ec-a287-cec850c707e0)。  
  
 您可於[在專案外](../windows/how-to-open-a-resource-script-file-outside-of-a-project-standalone.md)開啟的 .rc 檔間使用此種拖放方法。  
  
### 若要使用拖放方法在檔案間複製資源  
  
1.  兩個資源檔都要獨立開啟 \(如需詳細資訊，請參閱[在專案外檢視 .rc 檔資源](../windows/how-to-open-a-resource-script-file-outside-of-a-project-standalone.md)\)。  例如，開啟 Source1.rc 和 Source2.rc。  
  
2.  在第一個 .rc 檔內，按一下您希望複製的資源。  例如，在 Source1.rc 中，按一下 IDD\_DIALOG1。  
  
3.  按住 CTRL 鍵，並將該資源拖曳到第二個 .rc 檔。  例如，將 IDD\_DIALOG1 從 Source1.rc 拖曳到 Source2.rc。  
  
    > [!NOTE]
    >  如果沒有按住 CTRL 鍵便拖曳資源，就只會移動資源而不是複製資源。  
  
### 若要使用複製和貼上複製資源  
  
1.  兩個資源檔都要獨立開啟 \(如需詳細資訊，請參閱[在專案外檢視 .rc 檔資源](../windows/how-to-open-a-resource-script-file-outside-of-a-project-standalone.md)\)。  例如，Source1.rc 和 Source2.rc。  
  
2.  在希望從中複製資源的原始程式檔 \(例如，Source1.rc\) 中，在該資源上按一下滑鼠右鍵，然後從捷徑功能表中選擇 \[複製\]。  
  
3.  在希望貼入該資源的資源檔 \(例如，Source2.rc\) 上按一下滑鼠右鍵。  從捷徑功能表中選擇 \[貼上\]。  
  
    > [!NOTE]
    >  您無法在專案的資源檔 \(\[資源檢視\]\) 與獨立的 .rc 檔 \(開啟於文件視窗的檔案\) 之間進行拖放、複製、剪下或貼上等作業。  您可本產品舊版中執行這類作業。  
  
    > [!NOTE]
    >  為了避免與現有檔案符號名稱或值發生衝突，Visual C\+\+ 可能會在您將資源複製到新檔案時，變更傳輸的資源符號值或符號名稱和值。  
  
 如需將資源加入至 Managed 專案的詳細資訊，請參閱《.NET Framework 開發人員手冊》中的[應用程式中的資源](../Topic/Resources%20in%20Desktop%20Apps.md)。 如需手動將資源加入至 Managed 專案、存取資源、顯示靜態資源和指定屬性的資源字串等詳細資訊，請參閱[逐步解說：將 Windows Form 當地語系化](http://msdn.microsoft.com/zh-tw/9a96220d-a19b-4de0-9f48-01e5d82679e5)和[Walkthrough: Using Resources for Localization with ASP.NET](../Topic/Walkthrough:%20Using%20Resources%20for%20Localization%20with%20ASP.NET.md)。  
  
 需求  
  
 Win32  
  
## 請參閱  
 [How to: Open a Resource Script File Outside of a Project \(Standalone\)](../windows/how-to-open-a-resource-script-file-outside-of-a-project-standalone.md)   
 [Resource Files](../mfc/resource-files-visual-studio.md)   
 [Resource Editors](../mfc/resource-editors.md)