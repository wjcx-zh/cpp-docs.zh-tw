---
title: "建立專案 (ATL 教學課程，第 1 部分) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "get-started-article"
dev_langs: 
  - "C++"
ms.assetid: f6b727d1-390a-4b27-b82f-daadcd9fc059
caps.latest.revision: 16
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 建立專案 (ATL 教學課程，第 1 部分)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

本指南透過建立 ActiveX 物件的多邊形的非屬性化 ATL 專案逐步為您解說。  物件包含允許的使用者選項變更組成多邊形和程式碼的邊數重新整理顯示。  
  
> [!NOTE]
>  ATL 和 MFC 在 Visual Studio 的 Express 版本通常不支援。  
  
> [!NOTE]
>  本教學課程中建立原始程式碼和 POLYGON 範例相同。  如果您要避免手動輸入原始程式碼，可以從 [POLYGON 範例摘要](../top/visual-cpp-samples.md)。  您可以參考多邊形原始程式碼，將本指南工作，或使用它來檢查專案中的錯誤。  
  
### 若要建立初始 ATL 專案使用 ATL 專案精靈  
  
1.  在 Visual Studio 開發環境中，按一下 \[**檔案**\] 功能表上的 \[**新增**\] \]，然後按一下 \[**專案**\]。  
  
2.  按一下 \[**Visual C\+\+ 專案**\] 資料夾並選取 \[**ATL 專案**\]。  
  
3.  輸入 `多邊形` ，專案名稱。  
  
     原始程式碼的位置通常會預設為 My Documents \\ Visual Studio Projects，因此，新資料夾會自動建立。  
  
4.  按一下 \[**OK**\] 和 ATL 專案精靈隨即開啟。  
  
5.  請按一下 \[**應用程式設定**\] 索引標籤中的可用。  
  
6.  當您建立控制項，因此，控制項必須是同處理序伺服程式，將 \[**應用程式類型**\] 保留為 DLL。  
  
7.  保留其他選項在其預設值，然後按一下 \[**結束**\]。  
  
 ATL 專案精靈會產生數個檔案建立專案。  您可以展開多邊形物件檢視在方案總管中的這些檔案。  檔案列示如下。  
  
|檔案|描述|  
|--------|--------|  
|Polygon.cpp|包含 `DllMain`、 `DllCanUnloadNow`、 `DllGetClassObject`、 `DllRegisterServer`和 `DllUnregisterServer`的實作。  同時包含物件對應，是您專案中的 ATL 物件清單。  這個一開始是空白的。|  
|Polygon.def|這個模組定義檔提供連結器有關您的 DLL 所需之匯出的資訊。|  
|Polygon.idl|介面定義語言 \(IDL\) 檔案，描述介面專屬的物件。|  
|Polygon.rgs|這個指令碼包含登錄的程式 DLL 的資訊。|  
|Polygon.rc|資源檔，原先包含專案名稱的版本資訊和資料。|  
|Resource.h|資源檔的標頭檔 \(Header File\)。|  
|Polygonps.def|這個模組定義檔提供連結器有關的 Proxy 和 Stub 程式碼需要匯出資訊跨 Apartment 的支援呼叫。|  
|stdafx.cpp|將 `#include` ATL 實作的檔案。|  
|stdafx.h|將 `#include` ATL 標頭檔的檔案。|  
  
1.  在方案總管中，以滑鼠右鍵按一下 `Polygon` 專案。  
  
2.  在捷徑功能表上，按一下 \[**屬性**\]。  
  
3.  按一下 \[**連結器**\]。  變更 \[**每位使用者**\] 的 \[**重新導向**\] 索引標籤加入至 \[**是**\]。  
  
4.  按一下 \[**確定**\]。  
  
 在下一個步驟中，您會將控制項加入至您的專案。  
  
 [在步驟 2](../atl/adding-a-control-atl-tutorial-part-2.md)  
  
## 請參閱  
 [教學課程](../atl/active-template-library-atl-tutorial.md)