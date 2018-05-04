---
title: 匯出 （匯出函式） |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- VC.Project.VCLinkerTool.ExportFunctions
- /export
dev_langs:
- C++
helpviewer_keywords:
- /EXPORT linker option
- EXPORT linker option
- -EXPORT linker option
ms.assetid: 0920fb44-a472-4091-a8e6-73051f494ca0
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f366b40e8e40e62f67ec45f3e59ad61eb338c427
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="export-exports-a-function"></a>/EXPORT (匯出函式)
```  
/EXPORT:entryname[,@ordinal[,NONAME]][,DATA]  
```  
  
## <a name="remarks"></a>備註  
 使用此選項，您可以從您的程式匯出函式，可讓其他程式可以呼叫此函式。 您也可以匯出資料。 匯出通常被定義在 DLL 中。  
  
 *Entryname*是函式或資料的項目名稱，因為它是可供呼叫端程式。 `ordinal` 指定介於 1 到 65535 之間的匯出資料表的索引如果您未指定`ordinal`，連結會指派一個。 **NONAME**關鍵字匯出函式只能做為序數，而不*entryname*。  
  
 **資料**關鍵字會指定匯出的項目是資料的項目。 必須使用宣告中的用戶端程式的資料項目**extern __declspec （dllimport)**。  
  
 有三種方法匯出定義，建議使用的順序中所列：  
  
1.  [__declspec （dllexport)](../../cpp/dllexport-dllimport.md)原始碼中  
  
2.  [匯出](../../build/reference/exports.md).def 檔案中的陳述式  
  
3.  LINK 命令中 /EXPORT 規格  
  
 這三個方法可以使用相同程式中。 當連結建置包含匯出的程式時，它也會建立匯入程式庫，除非組建中使用.exp 檔。  
  
 連結使用裝飾形式的識別項。 建立的.obj 檔案時，編譯器會裝飾識別項。 如果*entryname*指定至連結器在其未裝飾形成 （因為它會出現在原始碼），連結會嘗試比對的名稱。 如果找不到唯一的相符項目，連結就會發出錯誤訊息。 使用[DUMPBIN](../../build/reference/dumpbin-reference.md)工具，以取得[裝飾名稱](../../build/reference/decorated-names.md)表單時，您必須指定至連結器識別項。  
  
> [!NOTE]
>  未指定裝飾的形式的宣告 C 識別項`__cdecl`或`__stdcall`。  
  
### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個連結器選項  
  
1.  開啟專案的 [屬性頁]  對話方塊。 如需詳細資訊，請參閱[設定 Visual c + + 專案屬性](../../ide/working-with-project-properties.md)。  
  
2.  按一下**連結器**資料夾。  
  
3.  按一下 [命令列]  屬性頁。  
  
4.  輸入到選項**其他選項**方塊。  
  
### <a name="to-set-this-linker-option-programmatically"></a>若要以程式設計方式設定這個連結器選項  
  
-   請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AdditionalOptions%2A>。  
  
## <a name="see-also"></a>另請參閱  
 [設定連結器選項](../../build/reference/setting-linker-options.md)   
 [連結器選項](../../build/reference/linker-options.md)