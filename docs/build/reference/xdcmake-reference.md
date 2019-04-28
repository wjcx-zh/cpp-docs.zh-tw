---
title: XDCMake 參考
ms.date: 11/04/2016
f1_keywords:
- xdcmake
helpviewer_keywords:
- xdcmake program
ms.assetid: 14e65747-d000-4343-854b-8393bf01cbac
ms.openlocfilehash: 097c105e005a3c734ba86139ed3b4b6ecdcf49d9
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62316388"
---
# <a name="xdcmake-reference"></a>XDCMake 參考

xdcmake.exe 是一種程式，可將.xdc 檔案編譯成.xml 檔案。 MSVC 編譯器的每個原始程式碼檔案建立.xdc 檔案編譯原始程式碼時[/doc](doc-process-documentation-comments-c-cpp.md)和原始程式碼檔包含標示的 XML 標記的文件註解時。

### <a name="to-use-xdcmakeexe-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中使用 xdcmake.exe

1. 開啟專案的 [屬性頁]  對話方塊。 如需詳細資訊，請參閱 <<c0> [ 設定C++Visual Studio 中的編譯器和組建屬性](../working-with-project-properties.md)。</c0>

1. 開啟 [組態屬性] 資料夾。

1. 按一下 [XML 文件註解] 屬性頁。

> [!NOTE]
>  命令列中的 xdcmake.exe 選項與用於開發環境 (屬性頁) 中的 xdcmake.exe 選項不同。 如需在開發環境中使用 xdcmake.exe 的資訊，請參閱 [XML 文件產生器工具屬性頁](xml-document-generator-tool-property-pages.md)。

## <a name="syntax"></a>語法

xdcmake `input_filename options`

## <a name="parameters"></a>參數

*input_filename*<br/>
用作 xdcmake.exe 輸入之 .xdc 檔案的檔案名稱。 指定一或多個 .xdc 檔案，或使用 *.xdc 以使用目前目錄中的所有 .xdc 檔案。

*options*<br/>
下列零或多項：

|選項|描述|
|------------|-----------------|
|/?、/help|顯示 xdcmake.exe 的說明。|
|/assembly:*filename*|讓您指定 .xml 檔案中 \<assembly> 標籤的值。  根據預設，\<assembly> 標籤的值與 .xml 檔案的檔名相同。|
|/nologo|隱藏著作權訊息。|
|/out:*filename*|讓您指定 .xml 檔案的名稱。  根據預設，.xml 檔案的名稱是 xdcmake.exe 所處理之第一個 .xdc 檔案的檔名。|

## <a name="remarks"></a>備註

建置專案時，Visual Studio 會自動叫用 xdcmake.exe。 您也可以從命令列叫用 xdcmake.exe。

如需將文件註解新增至原始程式碼檔的詳細資訊，請參閱[建議使用的文件註解標籤](recommended-tags-for-documentation-comments-visual-cpp.md)。

## <a name="see-also"></a>另請參閱

[XML 文件](xml-documentation-visual-cpp.md)
