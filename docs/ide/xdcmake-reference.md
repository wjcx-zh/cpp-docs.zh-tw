---
title: XDCMake 參考 | Microsoft Docs
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
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33333901"
---
# <a name="xdcmake-reference"></a>XDCMake 參考
xdcmake.exe 是一種程式，可將.xdc 檔案編譯成.xml 檔案。 Visual C++ 會在下列情況下為每個原始程式碼檔建立 .xdc 檔案：當原始程式碼以 [/doc](../build/reference/doc-process-documentation-comments-c-cpp.md) 編譯時，以及當原始程式碼檔包含以 XML 標籤標記的文件註解時。  
  
### <a name="to-use-xdcmakeexe-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中使用 xdcmake.exe  
  
1.  開啟專案的 [屬性頁]  對話方塊。 如需詳細資料，請參閱[使用專案屬性](../ide/working-with-project-properties.md)。  
  
2.  開啟 [組態屬性] 資料夾。  
  
3.  按一下 [XML 文件註解] 屬性頁。  
  
> [!NOTE]
>  命令列中的 xdcmake.exe 選項與用於開發環境 (屬性頁) 中的 xdcmake.exe 選項不同。 如需在開發環境中使用 xdcmake.exe 的資訊，請參閱 [XML 文件產生器工具屬性頁](../ide/xml-document-generator-tool-property-pages.md)。  
  
## <a name="syntax"></a>語法  
 xdcmake `input_filename options`  
  
## <a name="parameters"></a>參數  
 其中：  
  
 `input_filename`  
 用作 xdcmake.exe 輸入之 .xdc 檔案的檔案名稱。 指定一或多個 .xdc 檔案，或使用 *.xdc 以使用目前目錄中的所有 .xdc 檔案。  
  
 `options`  
 下列零或多項：  
  
|選項|描述|  
|------------|-----------------|  
|/?、/help|顯示 xdcmake.exe 的說明。|  
|/assembly:*filename*|讓您指定 .xml 檔案中 \<assembly> 標籤的值。  根據預設，\<assembly> 標籤的值與 .xml 檔案的檔名相同。|  
|/nologo|隱藏著作權訊息。|  
|/out:*filename*|讓您指定 .xml 檔案的名稱。  根據預設，.xml 檔案的名稱是 xdcmake.exe 所處理之第一個 .xdc 檔案的檔名。|  
  
## <a name="remarks"></a>備註  
 建置專案時，Visual Studio 會自動叫用 xdcmake.exe。 您也可以從命令列叫用 xdcmake.exe。  
  
 如需將文件註解新增至原始程式碼檔的詳細資訊，請參閱[建議使用的文件註解標籤](../ide/recommended-tags-for-documentation-comments-visual-cpp.md)。  
  
## <a name="see-also"></a>請參閱  
 [XML 文件](../ide/xml-documentation-visual-cpp.md)