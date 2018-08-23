---
title: -SUBSYSTEM （指定子系統） |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /subsystem
- VC.Project.VCLinkerTool.SubSystem
- VC.Project.VCLinkerTool.SubSystemVersion
dev_langs:
- C++
helpviewer_keywords:
- /SUBSYSTEM linker option
- SUBSYSTEM linker option
- -SUBSYSTEM linker option
- subsystem specifications
ms.assetid: d7b133cf-cf22-4da8-ab46-6552702c0b9b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a40cf81d0b00123692c9ea8b0e2f3111fb914fbb
ms.sourcegitcommit: a41c4d096afca1e9b619bbbce045b77135d32ae2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/14/2018
ms.locfileid: "42573030"
---
# <a name="subsystem-specify-subsystem"></a>/SUBSYSTEM (指定子系統)
```  
/SUBSYSTEM:{BOOT_APPLICATION|CONSOLE|EFI_APPLICATION|  
            EFI_BOOT_SERVICE_DRIVER|EFI_ROM|EFI_RUNTIME_DRIVER|NATIVE|  
            POSIX|WINDOWS)  
            [,major[.minor]]  
```  
  
 BOOT_APPLICATION  
 在 Windows 開機環境中執行的應用程式。 如需有關開機應用程式的詳細資訊，請參閱 <<c0> [ 關於 BCD](http://msdn.microsoft.com/library/windows/desktop/aa362639)。  
  
 主控台  
 Win32 字元模式應用程式。 作業系統會提供主控台的主控台應用程式。 如果`main`或`wmain`原生程式碼，定義`int main(array<String ^> ^)`定義為 managed 程式碼，或您使用建置應用程式完全`/clr:safe`，主控台是預設值。  
  
 可延伸韌體介面  
 EFI_ * 子系統。 如需詳細資訊的 EFI 規格，請參閱。 例如，請參閱 Intel 網站。 最小值及預設的版本為 1.0。  
  
 原生  
 針對 Windows NT 核心模式驅動程式。 此選項通常保留給 Windows 系統元件。 如果[/driver: wdm](../../build/reference/driver-windows-nt-kernel-mode-driver.md)指定，則原生是預設值。  
  
 POSIX  
 使用 Windows NT 中的 POSIX 子系統中執行的應用程式。  
  
 視窗  
 應用程式不需要主控台中，可能因為它會建立自己的使用者互動的視窗。 如果`WinMain`或是`wWinMain`定義原生程式碼，或`WinMain(HISTANCE *, HINSTANCE *, char *, int)`或`wWinMain(HINSTANCE *, HINSTANCE *, wchar_t *, int)`定義 managed 程式碼，WINDOWS 會是預設值。  
  
 `Major` 和`minor`（選擇性）  
 指定之子系統的最小必要的版本。 引數是介於 0 到 65535 的十進位數字。 請參閱的 < 備註 > 的詳細資訊。 沒有版本號碼的上限。  
  
## <a name="remarks"></a>備註  
 /SUBSYSTEM 選項會指定可執行檔的環境。  
  
 子系統的選擇會影響進入點符號 （或進入點函式），連結器將會選取。  
  
 選擇性的最小值和預設`major`和`minor`的子系統版本號碼為，如下所示。  
  
|子系統|最低|預設|  
|---------------|-------------|-------------|  
|BOOT_APPLICATION|1.0|1.0|  
|主控台|5.01 (x86) (x64) 5.02 6.02 (ARM)|（x86、 x64） 的 6.00 6.02 (ARM)|  
|視窗|5.01 (x86) (x64) 5.02 6.02 (ARM)|（x86、 x64） 的 6.00 6.02 (ARM)|  
|（與驅動程式： WDM) 的原生|(x86) 1.00 1.10 (x64、 ARM)|(x86) 1.00 1.10 (x64、 ARM)|  
|（不含 /driver: wdm) 的原生|4.00 (x86) (x64) 5.02 6.02 (ARM)|4.00 (x86) (x64) 5.02 6.02 (ARM)|  
|POSIX|1.0|19.90|  
|EFI_APPLICATION，EFI_BOOT_SERVICE_DRIVER，EFI_ROM EFI_RUNTIME_DRIVER|1.0|1.0|  
  
### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個連結器選項  
  
1.  開啟專案的 [屬性頁]  對話方塊。 如需詳細資訊，請參閱 <<c0> [ 設定 Visual c + + 專案屬性](../../ide/working-with-project-properties.md)。  
  
2.  選取 [連結器] 資料夾。  
  
3.  選取 **系統**屬性頁。  
  
4.  修改`SubSystem`屬性。  
  
### <a name="to-set-this-linker-option-programmatically"></a>若要以程式設計方式設定這個連結器選項  
  
-   請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.SubSystem%2A>。  
  
## <a name="see-also"></a>另請參閱  
 [設定連結器選項](../../build/reference/setting-linker-options.md)   
 [連結器選項](../../build/reference/linker-options.md)