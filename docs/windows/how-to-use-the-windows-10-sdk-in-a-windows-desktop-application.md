---
title: "如何： 使用 Windows 10 SDK 中的 Windows 桌面應用程式 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: get-started-article
dev_langs: C++
ms.assetid: eed6421e-9355-44a6-9582-3f1d453a6d44
caps.latest.revision: "4"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 1f5e6f09b371c4d295b4bcdff469396a2671d22a
ms.sourcegitcommit: 54035dce0992ba5dce0323d67f86301f994ff3db
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/03/2018
---
# <a name="how-to-use-the-windows-10-sdk-in-a-windows-desktop-application"></a>如何：在 Windows 桌面應用程式中使用 Windows 10 SDK
當您建立傳統 Windows 桌面專案在 Visual Studio 2017 時，它會設定預設使用 c + + 桌面工作負載已安裝，或上次更新時已安裝的 Windows 10 sdk 版本來建置。 這個 Windows SDK 版本是與所有最新的 Windows 版本相容。 如果您想要以較早版本的 SDK 為目標，您可以開啟專案 |屬性，然後選擇 從可用的 Windows SDK 版本下拉式清單中的其他 SDK 版本。  
  
 Visual Studio 2015 及 Windows 10 SDK 起，CRT 程式庫已分成兩個部分 (ucrtbase) 包含函式可接受用於通用 Windows 應用程式，以及包含其他項目 (vcruntime140)。 由於 Windows 10 SDK 包含新的函式，例如許多 C99 函式，因此您必須遵循下列步驟以使用這些函式。 請參閱 [CRT 程式庫的功能](../c-runtime-library/crt-library-features.md)。  
  
### <a name="to-target-the-windows-10-sdk"></a>以 Windows 10 SDK 為目標  
  
1.  確定已安裝 Windows 10 SDK。 Windows 10 SDK 安裝的一部份[Tools for Windows 10](http://go.microsoft.com/fwlink/p/?linkid=617631)。  
  
2.  開啟專案節點的捷徑功能表，然後選擇 [重定 SDK 版本目標] 。  
  
     ![將目標重定 SDK 版本](../windows/media/retargetingwindowssdk1.PNG "RetargetingWindowsSDK1")  
  
     [檢閱方案動作]  對話方塊隨即出現。  
  
     ![檢閱方案動作](../windows/media/retargetingwindowssdk2.PNG "RetargetingWindowsSDK2")  
  
3.  在**目標平台版本**下拉式清單中，選擇您要當做目標的 Windows 10 sdk 版本。 選擇 [確定] 按鈕以套用變更。  
  
     請注意，此處的 8.1 是指 Windows SDK 版本，該版本也與舊版 Windows 8、Windows Server 2012、Windows 7、Windows Server 2008 和 Windows Vista 相容。  
  
     如果這個步驟成功，則會在 [輸出] 視窗中顯示下列文字：  
  
     `Retargeting End: 1 completed, 0 failed, 0 skipped`  
  
4.  開啟專案屬性，在 [組態屬性]、[一般]  區段中，注意 [Windows 目標平台版本] 的值。 變更此處的值，會與遵循這個程序有相同的效果。 請參閱 [General Property Page (Project)](../ide/general-property-page-project.md)。  
  
     ![平台版本為目標](../windows/media/retargetingwindowssdk3.PNG "RetargetingWindowsSDK3")  
  
     這個動作會變更專案巨集的值，包括標頭檔和程式庫檔案的路徑。 若要查看變更的內容，在 Visual c + + 目錄 區段中的 專案屬性 對話方塊中，選擇其中一個 Include 目錄 等屬性，以開啟下拉式清單中，然後選擇 \<編輯 >。 [Include 目錄]  對話方塊隨即出現。  
  
     ![包含目錄對話方塊](../windows/media/retargetingwindowssdk4.PNG "RetargetingWindowsSDK4")  
  
     選擇**巨集 >>**按鈕，然後向下捲動至 Windows SDK 巨集，以查看所有新的值的巨集的清單。  
  
     ![Windows SDK 巨集](../windows/media/retargetingwindowssdk5.PNG "RetargetingWindowsSDK5")  
  
5.  如有需要，請針對其他專案重複步驟，並重建方案。  
  
### <a name="to-target-the-windows-81-sdk"></a>以 Windows 8.1 SDK 為目標  
  
1.  開啟專案節點的捷徑功能表，然後選擇 [重定 SDK 版本目標] 。  
  
2.  在 [目標平台版本] 下拉式清單中，選擇 8.1。  
  
## <a name="see-also"></a>請參閱  
 [Windows 桌面應用程式 （Visual c + +）](../windows/how-to-use-the-windows-10-sdk-in-a-windows-desktop-application.md)
