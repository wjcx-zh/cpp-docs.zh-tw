---
title: -INTEGRITYCHECK （需要簽章檢查） |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
dev_langs:
- C++
ms.assetid: 9e738825-2c98-40cd-8ad2-5d0d9c14893e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 997e3f5bb79ee3cbfa95c5762b0d3e998c56f362
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="integritycheck-require-signature-check"></a>/INTEGRITYCHECK (需要簽章檢查)
指定必須檢查在載入時間的二進位檔映像的數位簽章。  
  
```  
/INTEGRITYCHECK[:NO]  
```  
  
## <a name="remarks"></a>備註  
 根據預設， **/INTEGRITYCHECK**已關閉。  
  
 **/INTEGRITYCHECK**選項集-在 DLL 檔案或可執行檔的 PE 標頭 — 檢查數位簽章若要載入的映像中 Windows 記憶體管理員的旗標。 如果 32 位元和 64 位元 DLL 實作特定 Windows 功能載入的核心模式程式碼，必須設定這個選項，而且建議 Windows Vista、[!INCLUDE[win7](../../build/includes/win7_md.md)]、[!INCLUDE[win8](../../build/reference/includes/win8_md.md)]、[!INCLUDE[winsvr08](../../build/reference/includes/winsvr08_md.md)] 和 [!INCLUDE[winserver8](../../build/reference/includes/winserver8_md.md)] 的所有裝置驅動程式使用這個選項。 在 Windows Vista 之前的 Windows 版本會忽略此旗標。 如需詳細資訊，請參閱[強制完整性簽章的可攜式執行檔 (PE) 檔案](http://social.technet.microsoft.com/wiki/contents/articles/255.forced-integrity-signing-of-portable-executable-pe-files.aspx)。  
  
### <a name="to-set-this-linker-option-in-visual-studio"></a>在 Visual Studio 中設定這個連結器選項  
  
1.  開啟專案的 [ **屬性頁** ] 對話方塊。 如需詳細資訊，請參閱[使用專案屬性](../../ide/working-with-project-properties.md)。  
  
2.  展開**組態屬性**節點。  
  
3.  展開**連結器**節點。  
  
4.  選取**命令列**屬性頁。  
  
5.  在**其他選項**，輸入`/INTEGRITYCHECK`或`/INTEGRITYCHECK:NO`。  
  
## <a name="see-also"></a>另請參閱  
 [設定連結器選項](../../build/reference/setting-linker-options.md)   
 [連結器選項](../../build/reference/linker-options.md)   
 [強制的完整性簽章的可攜式執行檔 (PE) 檔案](http://social.technet.microsoft.com/wiki/contents/articles/255.forced-integrity-signing-of-portable-executable-pe-files.aspx)   
 [核心模式程式碼簽署逐步解說](http://msdn.microsoft.com/windows/hardware/gg487328.aspx)   
 [Windows 7 和 Windows Server 2008 中 AppInit Dll](http://msdn.microsoft.com/windows/hardware/gg463040.aspx)