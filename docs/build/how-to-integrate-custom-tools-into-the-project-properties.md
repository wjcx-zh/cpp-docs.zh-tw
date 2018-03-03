---
title: "如何： 將自訂工具整合至專案屬性 |Microsoft 文件"
ms.custom: 
ms.date: 04/27/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- msbuild.cpp.howto.integratecustomtools
dev_langs:
- C++
helpviewer_keywords:
- 'msbuild (c++), howto: integrate custom tools'
ms.assetid: f32d91a4-44e9-4de3-aa9a-1c7f709ad2ee
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: a762fc573953bcfb09180b9b830b761448d87a0d
ms.sourcegitcommit: 54035dce0992ba5dce0323d67f86301f994ff3db
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/03/2018
---
# <a name="how-to-integrate-custom-tools-into-the-project-properties"></a>如何：將自訂工具整合至專案屬性中
您可以加入 Visual Studio 中的自訂工具選項**屬性頁**視窗所建立的基礎 XML 結構描述檔案。  
  
 **組態屬性**區段**屬性頁**視窗會顯示設定群組，稱為*規則*。 每個規則包含一種工具或功能群組的設定。 例如，**連結器**規則包含連結器工具的設定。 在規則中的設定可以再細分為*類別*。  
  
 本文件說明如何在設定的目錄，其中包含您的自訂工具的內容，讓 Visual Studio 啟動時載入內容中建立檔案。 如何修改檔案的相關資訊，請參閱[平台擴充性第 2 部分](http://go.microsoft.com/fwlink/p/?linkid=191489)Visual Studio 專案團隊部落格上。  
  
### <a name="to-add-or-change-project-properties"></a>若要新增或變更專案屬性  
  
1.  在 XML 編輯器中，建立 XML 檔案。  
  
2.  將檔案儲存在 Visual Studio 2017`VCTargets\1033`資料夾。 您必須已安裝的 Visual Studio 2017 的每個版本和每個語言的不同路徑。 例如，英文版的 Visual Studio Enterprise 版本的資料夾路徑是`%ProgramFiles%\Microsoft Visual Studio\2017\Enterprise\Common7\IDE\VC\VCTargets\1033`。 調整您的語言和 Visual Studio 版本的路徑。 在每個規則**屬性頁**視窗由這個資料夾中的 XML 檔案。 請確定檔案唯一名稱的資料夾中。  
  
3.  將內容複製`%ProgramFiles%\Microsoft Visual Studio\2017\<VS Edition>\Common7\IDE\VC\VCTargets\<LCID>\cl.xml`，關閉但不儲存變更，然後將內容貼在新的 XML 檔案。 您可以使用任何 XML 結構描述檔案-這只是其中一個可讓您從範本開始。  
  
4.  在新的 XML 檔案中，修改內容根據您的需求。 請務必變更**規則名稱**和**Rule.DisplayName**檔案頂端。  
  
5.  儲存變更並關閉檔案。  
  
6.  中的 XML 檔案`%ProgramFiles%\Microsoft Visual Studio\2017\<VS Edition>\Common7\IDE\VC\VCTargets\<LCID>`Visual Studio 啟動時載入。 因此，若要測試新的檔案，重新啟動 Visual Studio。  
  
7.  在**方案總管 中**，以滑鼠右鍵按一下專案，然後按一下**屬性**。 在**屬性頁**視窗中的，在左窗格中，確認有新的節點，您的規則的名稱。  
  
## <a name="see-also"></a>請參閱  
 [MSBuild (Visual C++)](../build/msbuild-visual-cpp.md)
