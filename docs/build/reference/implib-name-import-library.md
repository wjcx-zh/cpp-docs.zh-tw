---
title: "-IMPLIB （名稱匯入程式庫） |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- /implib
- VC.Project.VCLinkerTool.ImportLIbrary
dev_langs:
- C++
helpviewer_keywords:
- IMPLIB linker option
- /IMPLIB linker option
- -IMPLIB linker option
- import libraries, overriding default name
ms.assetid: fe8f71ab-7055-41b5-8ef8-2b97cfa4a432
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 523fc171aa8df3d0b4c6e09909db7c2c1dc0b833
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="implib-name-import-library"></a>/IMPLIB (名稱匯入程式庫)
  
> /IMPLIB:*檔名*  
  
## <a name="parameters"></a>參數  
  
*filename*  
使用者指定的匯入程式庫名稱。 它會取代預設的名稱。  
  
## <a name="remarks"></a>備註  
  
/IMPLIB 選項會覆寫建置包含匯出的程式時，會建立連結的匯入程式庫的預設名稱。 預設名稱從主要輸出檔和擴充功能的基底名稱形成。 lib。 如果指定了一個或多個項目，程式會包含匯出：  
  
-   [__Declspec （dllexport)](../../cpp/dllexport-dllimport.md)的原始程式碼中的關鍵字  
  
-   [匯出](../../build/reference/exports.md).def 檔案中的陳述式  
  
-   [/EXPORT](../../build/reference/export-exports-a-function.md) LINK 命令中的規格  
  
 未建立匯入程式庫時，連結就會忽略 /IMPLIB。 如果沒有指定匯出，連結就不會建立匯入程式庫。 如果在組建中使用的匯出檔案，匯入程式庫已存在，而且不會建立一個，也會假設連結。 如需匯入程式庫和匯出檔案資訊，請參閱[LIB 參考](../../build/reference/lib-reference.md)。  
  
### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個連結器選項  
  
1.  開啟專案的 [屬性頁]  對話方塊。 如需詳細資訊，請參閱[設定 Visual c + + 專案屬性](../../ide/working-with-project-properties.md)。  
  
2.  按一下**連結器**資料夾。  
  
3.  按一下**進階**屬性頁。  
  
4.  修改**匯入程式庫**屬性。  
  
### <a name="to-set-this-linker-option-programmatically"></a>若要以程式設計方式設定這個連結器選項  
  
-   請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.ImportLibrary%2A>。  
  
## <a name="see-also"></a>請參閱  
 [設定連結器選項](../../build/reference/setting-linker-options.md)   
 [連結器選項](../../build/reference/linker-options.md)