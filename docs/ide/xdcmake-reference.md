---
title: XDCMake 參考 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
f1_keywords:
- xdcmake
dev_langs:
- C++
helpviewer_keywords:
- xdcmake program
ms.assetid: 14e65747-d000-4343-854b-8393bf01cbac
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 383347dc5cd1ce0dcadff6bdee802b90fd52e85d
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="xdcmake-reference"></a>XDCMake 參考
xdcmake.exe 是一種程式，將.xdc 檔編譯成.xml 檔案。 .Xdc 檔由每個原始程式碼檔的 Visual c + + 編譯器與編譯原始程式碼時[/doc](../build/reference/doc-process-documentation-comments-c-cpp.md)和原始程式碼檔時包含以 XML 標記標記的文件註解。  
  
### <a name="to-use-xdcmakeexe-in-the-visual-studio-development-environment"></a>若要在 Visual Studio 開發環境中使用 xdcmake.exe  
  
1.  開啟專案的 [屬性頁]  對話方塊。 如需詳細資訊，請參閱[使用專案屬性](../ide/working-with-project-properties.md)。  
  
2.  開啟**組態屬性**資料夾。  
  
3.  按一下**XML 文件註解**屬性頁。  
  
> [!NOTE]
>  xdcmake.exe 用於開發環境 （屬性頁） 時的選項不同 xdcmake.exe 選項在命令列。 如需使用 xdcmake.exe 開發環境中的資訊，請參閱[XML 文件產生器工具屬性頁](../ide/xml-document-generator-tool-property-pages.md)。  
  
## <a name="syntax"></a>語法  
 xdcmake `input_filename options`  
  
## <a name="parameters"></a>參數  
 其中：  
  
 `input_filename`  
 做為輸入 xdcmake.exe.xdc 檔的檔案名稱。 指定一或多個.xdc 檔，或使用 *.xdc 使用目前的目錄中的所有.xdc 檔。  
  
 `options`  
 零個或多個項目：  
  
|選項|描述|  
|------------|-----------------|  
|/？、 /help|顯示 xdcmake.exe 的說明。|  
|/assembly:*檔名*|可讓您指定的值\<組件 > 標記的.xml 檔案中。  根據預設，值\<組件 > 標記是.xml 檔案的檔案名稱相同。|  
|/nologo|隱藏著作權訊息。|  
|/out:*檔名*|可讓您指定的.xml 檔案名稱。  根據預設的.xml 檔案名稱是由 xdcmake.exe 處理第一個.xdc 檔的檔名。|  
  
## <a name="remarks"></a>備註  
 Visual Studio 會叫用 xdcmake.exe 自動建置專案時。 您也可以在命令列 xdcmake.exe 叫用。  
  
 請參閱[建議的文件註解標記](../ide/recommended-tags-for-documentation-comments-visual-cpp.md)如需將文件註解加入至原始程式檔的詳細資訊。  
  
## <a name="see-also"></a>另請參閱  
 [XML 文件](../ide/xml-documentation-visual-cpp.md)