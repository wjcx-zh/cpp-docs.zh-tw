---
title: "建立專案 (ATL 教學課程，第 1 部分) |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: get-started-article
dev_langs: C++
ms.assetid: f6b727d1-390a-4b27-b82f-daadcd9fc059
caps.latest.revision: "16"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 1a9a5fc9a0d2175a419bbc0fb1aacbc9ea25006c
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="creating-the-project-atl-tutorial-part-1"></a>建立專案 (ATL 教學課程，第 1 部分)
本教學課程會逐步引導您完成未使用屬性的 ATL 專案來建立顯示多邊形 ActiveX 物件。 物件包含的選項讓使用者變更邊的多邊形和程式碼以重新整理顯示的數目。  
  
> [!NOTE]
>  ATL 和 MFC 不通常支援 Visual Studio 的 Express 版本中。  
  
> [!NOTE]
>  本教學課程會建立為多邊形範例相同的原始程式碼。 如果您想要避免手動輸入的原始程式碼，您可以下載從[Polygon 範例摘要](../visual-cpp-samples.md)。 當您逐步進行教學課程中，或使用它來檢查您自己的專案中的錯誤，您就可以參考多邊形原始碼。  
  
### <a name="to-create-the-initial-atl-project-using-the-atl-project-wizard"></a>若要建立初始的 ATL 專案使用 ATL 專案精靈  
  
1.  在 Visual Studio 開發環境中，按一下 **新增**上**檔案**功能表，然後再按一下**專案**。  
  
2.  按一下**Visual c + + 專案**資料夾，然後選取**ATL 專案**。  
  
3.  型別`Polygon`做為專案名稱。  
  
     原始碼的位置通常會預設為 My Documents\Visual Studio 專案，並會自動建立新的資料夾。  
  
4.  按一下**確定**和 ATL 專案精靈 隨即開啟。  
  
5.  按一下**應用程式設定**以查看可用的選項。  
  
6.  當您要建立控制項，並必須是同處理序伺服器之後，保留**應用程式類型**為 DLL。  
  
7.  其他選項保留其預設值，然後按**完成**。  
  
 ATL 專案精靈會產生數個檔案來建立專案。 您可以展開多邊形物件，在 [方案總管] 中檢視這些檔案。 檔案如下所示。  
  
|檔案|描述|  
|----------|-----------------|  
|Polygon.cpp|包含實作`DllMain`， `DllCanUnloadNow`， `DllGetClassObject`， `DllRegisterServer`，和`DllUnregisterServer`。 也包含物件的對應，也就是您的專案中的 ATL 物件的清單。 這一開始是空白。|  
|Polygon.def|這個模組定義檔會提供連結器所需的 DLL 匯出的相關資訊。|  
|Polygon.idl|介面定義語言檔案，其中描述您物件的特定介面。|  
|Polygon.rgs|此登錄指令碼包含註冊您的程式 DLL 的資訊。|  
|Polygon.rc|資源檔，一開始包含版本資訊和包含的專案名稱的字串。|  
|偵錯工具|資源檔標頭檔。|  
|Polygonps.def|此模組定義檔會提供連結器支援跨 apartment 呼叫的匯出將 proxy 和虛設常式程式碼所需的相關資訊。|  
|stdafx.cpp|將檔案`#include`ATL 實作檔案。|  
|stdafx.h|將檔案`#include`ATL 標頭檔。|  
  
1.  在 [方案總管] 中，以滑鼠右鍵按一下`Polygon`專案。  
  
2.  在捷徑功能表，按一下 **屬性**。  
  
3.  按一下**連結器**。 變更**每 UserRedirection**選項設定為**是**。  
  
4.  按一下 [確定 **Deploying Office Solutions**]。  
  
 在下一個步驟中，您將控制項加入您的專案。  
  
 [至步驟 2](../atl/adding-a-control-atl-tutorial-part-2.md)  
  
## <a name="see-also"></a>請參閱  
 [教學課程](../atl/active-template-library-atl-tutorial.md)

