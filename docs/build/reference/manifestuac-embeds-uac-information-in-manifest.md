---
title: "-MANIFESTUAC （將 UAC 資訊內嵌資訊清單中） |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VC.Project.VCLinkerTool.UACUIAccess
- VC.Project.VCLinkerTool.UACExecutionLevel
- VC.Project.VCLinkerTool.EnableUAC
dev_langs: C++
helpviewer_keywords:
- /MANIFESTUAC linker option
- MANIFESTUAC linker option
- -MANIFESTUAC linker option
ms.assetid: 2d243c39-fa13-493c-b56f-d0d972a1603a
caps.latest.revision: "12"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 564c17336936866750d05137a7bcd101b3a6534d
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="manifestuac-embeds-uac-information-in-manifest"></a>/MANIFESTUAC (將 UAC 資訊內嵌在資訊清單中)
指定使用者帳戶控制 (UAC) 資訊是否內嵌於程式資訊清單中。  
  
## <a name="syntax"></a>語法  
  
```  
/MANIFESTUAC  
/MANIFESTUAC:NO  
/MANIFESTUAC:fragment  
/MANIFESTUAC:level=_level  
/MANIFESTUAC:uiAccess=_uiAccess  
```  
  
#### <a name="parameters"></a>參數  
 `fragment`  
 字串，包含`level`和`uiAccess`值。 如需詳細資訊，請參閱本主題稍後的 < 備註 > 一節。  
  
 `_level`  
 其中一個*asInvoker*， *highestAvailable*，或*requireAdministrator*。 預設為 asInvoker。 如需詳細資訊，請參閱本主題稍後的 < 備註 > 一節。  
  
 `_uiAccess`  
 如果您希望應用程式略過使用者介面保護層級，並將輸入放到桌面上更高權限的視窗，則為 `true`；否則為 `false`。 預設值為 `false`。 設定為`true`只能針對使用者介面的協助工具應用程式。  
  
## <a name="remarks"></a>備註  
 如果您指定多個 /MANIFESTUAC 選項，在命令列上的，輸入的最後一個的優先順序較高。  
  
 /MANIFESTUAC:level 的選項如下所示：  
  
-   `asInvoker`: 應用程式會執行相同的權限的啟動程序。 應用程式可以提升為較高的權限層級選取**系統管理員身分執行**。  
  
-   highestAvailable： 具有最高的權限等級，它可以將執行的應用程式。 如果啟動應用程式的使用者是 Administrators 群組的成員，則此選項 requireAdministrator 相同。 如果最高可用權限層級高於的開啟處理序層級，系統會提示輸入認證。  
  
-   requireAdministrator: 應用程式會執行與系統管理員權限。 啟動應用程式的使用者必須是 Administrators 群組的成員。 如果開啟處理序正在使用系統管理權限，系統會提示輸入認證。  
  
 您可以使用 /MANIFESTUAC:fragment 選項，在一個步驟中指定的層級和 uiAccess 值。 片段必須以下列形式：  
  
```  
"level=[ asInvoker | highestAvailable | requireAdministrator ] uiAccess=[ true | false ]"  
```  
  
### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個連結器選項  
  
1.  開啟專案的 [屬性頁]  對話方塊。 如需詳細資訊，請參閱[使用專案屬性](../../ide/working-with-project-properties.md)。  
  
2.  展開**組態屬性**節點。  
  
3.  展開**連結器**節點。  
  
4.  選取**資訊清單檔案**屬性頁。  
  
5.  修改**啟用使用者帳戶控制 (UAC)**， **UAC 執行層級**，和**UAC 略過 UI 保護**屬性。  
  
### <a name="to-set-this-linker-option-programmatically"></a>若要以程式設計方式設定這個連結器選項  
  
1.  請參閱<xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.EnableUAC%2A>、<xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.UACExecutionLevel%2A>和<xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.UACUIAccess%2A>。  
  
## <a name="see-also"></a>請參閱  
 [設定連結器選項](../../build/reference/setting-linker-options.md)   
 [連結器選項](../../build/reference/linker-options.md)