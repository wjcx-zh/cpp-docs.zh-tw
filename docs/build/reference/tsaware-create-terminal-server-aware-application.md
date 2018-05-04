---
title: -TSAWARE （建立終端伺服器感知應用程式） |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /tsaware
- VC.Project.VCLinkerTool.TerminalServerAware
dev_langs:
- C++
helpviewer_keywords:
- Terminal Server
- /TSAWARE linker option
- Terminal Server, Terminal Server-aware applications
- -TSAWARE linker option
- TSAWARE linker option
ms.assetid: fe1c1846-de5b-4839-b562-93fbfe36cd29
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e386c9024ea7736adb2766488c1c51c80ff7177b
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="tsaware-create-terminal-server-aware-application"></a>/TSAWARE (建立終端伺服器感知應用程式)
```  
/TSAWARE[:NO]  
```  
  
## <a name="remarks"></a>備註  
 /TSAWARE 選項會在程式映像的選擇性標頭的 IMAGE_OPTIONAL_HEADER DllCharacteristics 欄位中設定的旗標。 設定此旗標時，終端機伺服器將不會對應用程式進行某些變更。  
  
 當應用程式不是終端伺服器感知 （也稱為傳統應用程式） 時，終端機伺服器會讓某些舊版的應用程式，讓它在多使用者環境中正常運作的修改。 比方說，終端機伺服器將建立虛擬的 Windows 資料夾中的每個使用者取得除了取得系統的 Windows 目錄的 [Windows] 資料夾。 這可讓使用者存取他們自己的 INI 檔案。 此外，終端機伺服器可讓舊版應用程式的登錄一些調整。 這些修改緩慢的載入舊版的應用程式，終端機伺服器上。  
  
 如果終端伺服器感知應用程式，它必須依賴 INI 檔案都寫入**HKEY_CURRENT_USER**在安裝期間登錄。  
  
 如果您使用 /TSAWARE，而且您的應用程式仍會使用 INI 檔案，檔案會共用系統的所有使用者。 如果是可接受，您仍然可以連結 /TSAWARE; 您的應用程式否則，您必須使用 /tsaware: no。  
  
 /TSAWARE 選項會預設啟用適用於 Windows 和主控台應用程式。 請參閱[/SUBSYSTEM](../../build/reference/subsystem-specify-subsystem.md)和[/VERSION](../../build/reference/version-version-information.md)資訊。  
  
 /TSAWARE 不正確的驅動程式、 Vxd 或 Dll。  
  
 如果應用程式已連結 DUMPBIN，/TSAWARE [/HEADERS](../../build/reference/headers.md)會顯示說明該狀況的資訊。  
  
### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個連結器選項  
  
1.  開啟專案的 [屬性頁]  對話方塊。 如需詳細資訊，請參閱[設定 Visual c + + 專案屬性](../../ide/working-with-project-properties.md)。  
  
2.  按一下**連結器**資料夾。  
  
3.  按一下**系統**屬性頁。  
  
4.  修改**終端機伺服器**屬性。  
  
### <a name="to-set-this-linker-option-programmatically"></a>若要以程式設計方式設定這個連結器選項  
  
-   請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.TerminalServerAware%2A>。  
  
## <a name="see-also"></a>另請參閱  
 [設定連結器選項](../../build/reference/setting-linker-options.md)   
 [連結器選項](../../build/reference/linker-options.md)   
 [儲存使用者專屬資訊](http://msdn.microsoft.com/library/aa383452)   
 [在終端機服務環境中的舊版應用程式](https://msdn.microsoft.com/en-us/library/aa382957.aspx)