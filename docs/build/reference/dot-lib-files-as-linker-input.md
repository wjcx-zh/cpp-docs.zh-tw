---
title: .Lib 檔案做為連結器輸入 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- VC.Project.VCLinkerTool.AdditionalDependencies
dev_langs:
- C++
helpviewer_keywords:
- OMF libraries
- linking [C++], OMF libraries
- import libraries, linker files
- libraries [C++], .lib files as linker input
- COFF files, import libraries
- default libraries [C++], linker output
- default libraries [C++]
- defaults [C++], libraries
- .lib files
ms.assetid: dc5d2b1c-2487-41fa-aa71-ad1e0647958b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8382e43398c4b6e5241542e6b41fdee8e2f70eff
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32374540"
---
# <a name="lib-files-as-linker-input"></a>.Lib 檔做為連結器輸入
連結接受 COFF 標準程式庫和 COFF 匯入程式庫，這兩種通常有副檔名。 lib。 標準程式庫包含的物件，並且會 LIB 工具來建立。 匯入程式庫包含匯出的其他程式的相關資訊，而且會建立每個連結的建置包含匯出的程式時，或由 LIB 工具。 如需使用 LIB 建立標準或匯入程式庫的資訊，請參閱[LIB 參考](../../build/reference/lib-reference.md)。 如需使用連結來建立匯入程式庫的詳細資訊，請參閱[/DLL](../../build/reference/dll-build-a-dll.md)選項。  
  
連結指定程式庫做為檔名引數或預設程式庫。 連結解析外部參考搜尋命令列上指定的文件庫中的第一次，然後以指定程式庫的預設[/DEFAULTLIB](../../build/reference/defaultlib-specify-default-library.md)選項，接著在預設程式庫是具名.obj 檔中。 如果指定的路徑與程式庫名稱，連結會尋找該目錄中的程式庫。 如果未指定路徑，連結會尋找第一個連結，從執行目錄，然後再 LIB 環境變數中指定任何目錄中。  
  
## <a name="to-add-lib-files-as-linker-input-in-the-development-environment"></a>若要加入.lib 檔做為開發環境中的連結器輸入  
  
1.  開啟專案的 [屬性頁]  對話方塊。 如需詳細資訊，請參閱[使用專案屬性](../../ide/working-with-project-properties.md)。  
  
2.  選擇**輸入**中的 屬性頁**連結器**資料夾。  
  
3.  修改**其他相依性**屬性將.lib 檔案。  
  
## <a name="to-programmatically-add-lib-files-as-linker-input"></a>若要以程式設計方式加入.lib 檔做為連結器輸入  
  
-   請參閱[AdditionalDependencies](https://msdn.microsoft.com/library/microsoft.visualstudio.vcprojectengine.vclinkertool.additionaldependencies.aspx)。  
  
## <a name="example"></a>範例  
下列範例會示範如何建立及使用.lib 檔。 首先，建立.lib 檔：  
  
```cpp  
// lib_link_input_1.cpp  
// compile by using: cl /LD lib_link_input_1.cpp  
__declspec(dllexport) int Test() {  
   return 213;  
}  
```  
  
然後再編譯這個範例使用您剛才建立的.lib 檔：  
  
```cpp  
// lib_link_input_2.cpp  
// compile by using: cl /EHsc lib_link_input_1.lib lib_link_input_2.cpp   
__declspec(dllimport) int Test();  
#include <iostream>  
int main() {  
   std::cout << Test() << std::endl;  
}  
```  
  
```Output  
213  
```  
  
## <a name="see-also"></a>另請參閱  
 [LINK 輸入的檔](../../build/reference/link-input-files.md)   
 [連結器選項](../../build/reference/linker-options.md)