---
title: -DLL （建置 DLL） |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /dll
dev_langs:
- C++
helpviewer_keywords:
- -DLL linker option
- /DLL linker option [C++]
- exporting DLLs [C++], specifying exports
- DLLs [C++], building
- DLL linker option [C++]
ms.assetid: c7685aec-31d0-490f-9503-fb5171a23609
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 1767ac9ef063ace2ee9d567dd9038519afababf8
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32373071"
---
# <a name="dll-build-a-dll"></a>/DLL (建置 DLL)
```  
/DLL  
```  
  
## <a name="remarks"></a>備註  
 /DLL 選項建置 DLL 做為主要輸出檔。 DLL 通常包含可供其他程式的匯出。 有三種方法，可指定匯出，建議使用的順序中所列：  
  
1.  [__declspec （dllexport)](../../cpp/dllexport-dllimport.md)原始碼中  
  
2.  [匯出](../../build/reference/exports.md).def 檔案中的陳述式  
  
3.  [/EXPORT](../../build/reference/export-exports-a-function.md) LINK 命令中的規格  
  
 程式可以使用一個以上的方法。  
  
 建置 DLL 的另一個方法是使用**文件庫**模組定義陳述式。 /BASE 和 /DLL 選項放在一起即相當於**文件庫**陳述式。  
  
 未指定此選項，在開發環境。此選項為只在命令列上使用。 當您使用應用程式精靈建立 DLL 專案時，會設定這個選項。  
  
 請注意，是否您在預備步驟中，建立您匯入程式庫建立.dll 之前時，您必須傳遞相同的物件檔案集建置.dll 時為您成功建置匯入程式庫時。  
  
### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個連結器選項  
  
1.  開啟專案的 [屬性頁]  對話方塊。 如需詳細資訊，請參閱[設定 Visual c + + 專案屬性](../../ide/working-with-project-properties.md)。  
  
2.  按一下**組態屬性**資料夾。  
  
3.  按一下**一般**屬性頁。  
  
4.  修改**組態類型**屬性。  
  
### <a name="to-set-this-linker-option-programmatically"></a>若要以程式設計方式設定這個連結器選項  
  
-   請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCPropertySheet.ConfigurationType%2A>。  
  
## <a name="see-also"></a>另請參閱  
 [設定連結器選項](../../build/reference/setting-linker-options.md)   
 [連結器選項](../../build/reference/linker-options.md)