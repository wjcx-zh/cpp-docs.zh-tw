---
title: 基底 （基底位址） |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /base
- VC.Project.VCLinkerTool.BaseAddress
dev_langs:
- C++
helpviewer_keywords:
- base addresses [C++]
- programs [C++], preventing relocation
- semicolon [C++], specifier
- -BASE linker option
- key address size
- environment variables [C++], LIB
- programs [C++], base address
- LIB environment variable
- BASE linker option
- DLLs [C++], linking
- /BASE linker option
- '@ symbol for base address'
- executable files [C++], base address
- at sign symbol for base address
ms.assetid: 00b9f6fe-0bd2-4772-a69c-7365eb199069
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c4090a3e8d2f9f3bdcb68875d94a1b84e7bff0f3
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="base-base-address"></a>/BASE (基底位址)
```  
/BASE:{address[,size] | @filename,key}  
```  
  
 基底的選項設定的程式，覆寫.exe 或 DLL 檔的預設位置的基底位址。 32 位元映像的 0x400000 或 64 位元映像的 0x140000000.exe 檔案的預設起始位址。 為 dll，請預設基底地址是 0x10000000 32 位元映像或 0x180000000 64 位元映像。 在作業系統上不支援位址空間配置隨機載入 (ASLR)，或 /dynamicbase: no 選項已設定時，作業系統會先嘗試載入程式在其指定或預設的基底位址。 如果有足夠的空間無法使用有，在系統重新放置到該程式。 若要防止重新配置，請使用[/固定](../../build/reference/fixed-fixed-base-address.md)選項。  
  
 連結器會發出錯誤*位址*不是 64 K 的倍數。 您可以選擇性地指定該程式; 的大小如果您指定的大小不能配合程式連結器就會發出警告。  
  
 命令列上指定的基底位址的另一個方法是使用基底地址的回應檔。 基底位址的回應檔案是文字檔，其中包含基底位址及選擇性的所有 Dll 將使用您的程式，以及每個基底位址的唯一文字索引鍵的大小。 若要使用回應檔案，以指定的基底位址，使用 at 符號 (@) 回應檔的名稱，後面接著*filename*，後面接著一個逗號，則`key`檔案中使用的基底地址的值。 連結器會尋找*filename*中任一個指定的路徑，或如果沒有指定路徑，LIB 環境變數中指定之目錄中。 中的每一行*filename*代表一個 DLL，並具有下列語法：  
  
```  
  
key address [size] ;comment  
```  
  
 `key`是英數字元的字串，不區分大小寫。 它通常是 DLL，名稱，但不是需要。 `key`後面接著基底*位址*在 C 語言、 十六進位或十進位標記法和選擇性的最大`size`。 所有的三個引數會以空格或定位字元分隔。 連結器會發出警告指定`size`小於程式所需的虛擬位址空間。 A`comment`指定分號 （;），而且可以是在相同或不同的行上。 連結器會忽略從分號到行尾的所有文字。 此範例會顯示這類檔案的一部分：  
  
```  
main   0x00010000    0x08000000    ; for PROJECT.exe  
one    0x28000000    0x00100000    ; for DLLONE.DLL  
two    0x28100000    0x00300000    ; for DLLTWO.DLL  
```  
  
 如果檔案包含這些線條稱為 DLLS.txt，下列範例命令會套用這項資訊：  
  
```  
link dlltwo.obj /dll /base:@dlls.txt,two  
```  
  
## <a name="remarks"></a>備註  
 基於安全性理由，Microsoft 建議您使用[/DYNAMICBASE](../../build/reference/dynamicbase-use-address-space-layout-randomization.md)選項而不是指定您可執行檔的基底位址。 這會產生可執行映像可以是隨機重定基底在載入時使用 Windows 的位址空間配置隨機載入 (ASLR) 功能。 /DYNAMICBASE 選項預設為開啟。  
  
 設定基底地址的另一個方法是使用*基底*引數中的[名稱](../../build/reference/name-c-cpp.md)或[文件庫](../../build/reference/library.md)陳述式。 /BASE 和[/DLL](../../build/reference/dll-build-a-dll.md)選項放在一起即相當於**文件庫**陳述式。  
  
### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個連結器選項  
  
1.  開啟專案的 [屬性頁]  對話方塊。 如需詳細資訊，請參閱[設定 Visual c + + 專案屬性](../../ide/working-with-project-properties.md)。  
  
2.  展開**連結器**資料夾。  
  
3.  選擇**進階**屬性頁。  
  
4.  修改**基底位址**屬性。  
  
### <a name="to-set-this-linker-option-programmatically"></a>若要以程式設計方式設定這個連結器選項  
  
-   請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.BaseAddress%2A>。  
  
## <a name="see-also"></a>另請參閱  
 [設定連結器選項](../../build/reference/setting-linker-options.md)   
 [連結器選項](../../build/reference/linker-options.md)