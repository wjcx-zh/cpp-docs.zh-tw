---
title: "如何：在 Windows 桌面應用程式中使用 Windows 10 SDK  | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "get-started-article"
dev_langs: 
  - "C++"
ms.assetid: eed6421e-9355-44a6-9582-3f1d453a6d44
caps.latest.revision: 4
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 4
---
# 如何：在 Windows 桌面應用程式中使用 Windows 10 SDK 
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

當您在 [!INCLUDE[vs_dev14](../ide/includes/vs_dev14_md.md)] 中建立傳統 Windows 桌面專案時，預設會使用 Windows 8.1 SDK 執行建置作業。 這個 Windows SDK 版本與包括 Windows 10 在內的所有最新 Windows 版本相容，但不包含 Windows 10 SDK 中的最新 Windows 10 API 和 CRT 函式。 如果您想要使用新的 API，您可以將專案目標重定為參考 Windows 10 SDK。  
  
 從 [!INCLUDE[vs_dev14](../ide/includes/vs_dev14_md.md)] 和 Windows 10 SDK 開始，CRT 程式庫已分成兩個部分，其中一個部分 \(ucrtbase\) 包含可接受用於通用 Windows 應用程式的函式，另一個部分則包含其他任何函式 \(vcruntime140\)。 由於 Windows 10 SDK 包含新的函式，例如許多 C99 函式，因此您必須遵循下列步驟以使用這些函式。 請參閱 [CRT 程式庫功能](../c-runtime-library/crt-library-features.md)。  
  
### 以 Windows 10 SDK 為目標  
  
1.  確定已安裝 Windows 10 SDK。 Windows 10 SDK 會隨 [Tools for Windows 10](http://go.microsoft.com/fwlink/?LinkID=617631) 一起安裝。  
  
2.  開啟專案節點的捷徑功能表，然後選擇 \[重定 SDK 版本目標\]。  
  
     ![重定 SDK 版本目標](../windows/media/retargetingwindowssdk1.png "RetargetingWindowsSDK1")  
  
     \[檢閱方案動作\] 對話方塊隨即出現。  
  
     ![檢閱方案動作](../windows/media/retargetingwindowssdk2.png "RetargetingWindowsSDK2")  
  
3.  在 \[目標平台版本\] 下拉式清單中，選擇您想要設為目標的 Windows 10 SDK 版本；如果您不想要進行任何變更，請選擇 8.1。 選擇 \[確定\] 按鈕以套用變更。  
  
     請注意，此處的 8.1 是指 Windows SDK 版本，該版本也與舊版 Windows 8、Windows Server 2012、Windows 7、Windows Server 2008 和 Windows Vista 相容。  
  
     如果這個步驟成功，則會在 \[輸出\] 視窗中顯示下列文字：  
  
     `重定目標結束: 1 個完成，0 個失敗，0 個略過`  
  
4.  開啟專案屬性，在 \[組態屬性\]、\[一般\] 區段中，注意 \[Windows 目標平台版本\] 的值。 變更此處的值，會與遵循這個程序有相同的效果。 請參閱 [一般屬性頁 \(專案\)](../ide/general-property-page-project.md)。  
  
     ![目標平台版本](../windows/media/retargetingwindowssdk3.png "RetargetingWindowsSDK3")  
  
     這個動作會變更專案巨集的值，包括標頭檔和程式庫檔案的路徑。 若要查看已變更的內容，請在 \[專案屬性\] 對話方塊的 \[Visual C\+\+ 目錄\] 區段中，選擇 \[Include 目錄\] 等其中一個屬性以開啟下拉式清單，然後選擇 \[\<編輯\>\]。 \[Include 目錄\] 對話方塊隨即出現。  
  
     ![&#91;Include 目錄&#93; 對話方塊](../windows/media/retargetingwindowssdk4.png "RetargetingWindowsSDK4")  
  
     選擇 \[巨集 \>\>\] 按鈕，然後將巨集清單向下捲動至 Windows SDK 巨集，以查看所有新的值。  
  
     ![Windows SDK 巨集](../windows/media/retargetingwindowssdk5.png "RetargetingWindowsSDK5")  
  
5.  如有需要，請針對其他專案重複步驟，並重建方案。  
  
### 以 Windows 8.1 SDK 為目標  
  
1.  開啟專案節點的捷徑功能表，然後選擇 \[重定 SDK 版本目標\]。  
  
2.  在 \[目標平台版本\] 下拉式清單中，選擇 8.1。  
  
## 請參閱  
 [Windows Desktop Applications \(Visual C\+\+\)](../windows/how-to-use-the-windows-10-sdk-in-a-windows-desktop-application.md)