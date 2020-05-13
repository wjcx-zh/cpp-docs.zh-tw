---
title: MSVC 連結器參考
ms.date: 12/10/2018
ms.assetid: bb736587-d13b-4f3c-8982-3cc2c015c59c
ms.openlocfilehash: 2503e212e7325fc97f9057861cb85d5cf0571094
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81336491"
---
# <a name="linking"></a>連結

在C++專案中,*連結*步驟在編譯器將原始程式碼編譯為物件檔 (*.obj) 後執行。 連結器 (link.exe) 將物件檔合併到單個可執行檔中。

連結器選項可以設置在視覺工作室內外。 在 Visual Studio 中,您可以右鍵單擊**解決方案資源管理器**中的專案節點並選擇 **「屬性**」來顯示屬性頁,從而存取連結器選項。 在左邊窗格中選擇 **「連結器**」以展開節點並查看所有選項。

## <a name="linker-command-line-syntax"></a>連結器命令列語法

在 Visual Studio 外部執行 LINK 時,可以透過一種或多種方式指定輸入:

- 在命令列上

- 使用指令檔案

- 在環境變數中

LINK 首先處理在 LINK 環境變數中指定的選項,然後按照在命令列和命令檔中指定的選項的順序處理這些選項。 如果使用不同的參數重複一個選項,則最後處理的選項優先。

選項應用於整個生成;不能將任何選項應用於特定的輸入檔。

運行 LINK。EXE,使用以下命令語法:

```
LINK arguments
```

包括`arguments`選項和檔名,可以按任意順序指定。 首先處理選項,然後處理檔。 使用一個或多個空格或選項卡分隔參數。

> [!NOTE]
> 只能從可視化工作室命令提示符啟動此工具。 您無法從系統命令提示字元，或從 [檔案總管] 啟動它。

## <a name="command-line"></a>命令列

在命令列上,選項由選項指定器組成,即破折號 (-) 或向前斜杠 (/),後跟選項的名稱。 不能縮寫選項名稱。 某些選項採用在冒號(:))之後指定的參數。 選項規範中不允許空格或選項卡,但 /COMMENT 選項中的引用字串中除外。 以小數或 C 語言表示法指定數值參數。 選項名稱及其關鍵字或檔名參數不區分大小寫,但標識符作為參數區分大小寫。

要將檔案傳遞給連結器,請在 LINK 命令之後在命令列上指定檔名。 您可以使用檔案名指定絕對路徑或相對路徑,也可以在檔名中使用通配符。 如果省略點 (.) 和檔名副檔名,LINK 將假定 .obj 用於查找檔。 LINK 不使用檔案名副檔名或缺少文件副檔名來對文件內容進行假設;它通過檢查確定檔的類型,並相應地處理它。

link.exe 返回零以求成功(無錯誤)。  否則,連結器將返回停止連結的錯誤編號。  例如,如果連結器生成 LNK1104,則連結器返回 1104。  因此,連結器在錯誤時返回的最低錯誤數為 1000。  返回值 128 表示作業系統或 .config 檔的配置問題;載入程式未載入連結.exe或 c2.dll。

## <a name="link-command-files"></a>LINK 命令檔

可以將命令列參數以命令檔的形式傳遞給 LINK。 要向連結器指定指令檔案,請使用以下語法:

> **連結\@**<em>指令檔案</em>

*命令檔*是文字檔的名稱。 在 at 符**\@** 號 ( ) 和檔案名稱之間不允許空白或選項卡。 沒有預設擴展;因此,沒有預設擴展。必須指定完整的檔名,包括任何擴展名。 無法使用通配符。 您可以使用檔案名指定絕對路徑或相對路徑。 LINK 不使用環境變數來搜索檔。

在命令檔中,參數可以由空格或選項卡(如命令列)和換行符分隔。

您可以在命令檔中指定命令列的全部或部分。 您可以在 LINK 命令中使用多個命令檔。 LINK 接受命令檔輸入,就好像它是在命令行上的該位置指定的一樣。 無法嵌套命令檔。 LINK 與命令檔的內容相呼應,除非指定[了 /NOLOGO](nologo-suppress-startup-banner-linker.md)選項。

## <a name="example"></a>範例

產生 DLL 的以下指令會對象檔與函式庫的名稱傳遞到單獨的命令檔中,並使用第三個指令檔來規範 /EXPORTS 選項:

```cmd
link /dll @objlist.txt @liblist.txt @exports.txt
```

## <a name="link-environment-variables"></a>LINK 環境變數

LINK 工具使用下列環境變數：

- 連結和\_\_連結 ,如果已定義。 LINK 工具預先準備了 LINK 環境變數中定義的選項和參數,並在處理\_之前將\_LINK 環境變數中定義的選項和參數追加到命令列參數。

- LIB (若已定義)。 LINK 工具在搜索命令列或[/BASE](base-base-address.md)選項上指定的物件、庫或其他檔時使用 LIB 路徑。 它也會使用 LIB 路徑來尋找物件中指定的 .pdb 檔案。 LIB 變數可以包含一或多個以分號分隔的路徑規格。 一個路徑必須指向 Visual C++ 安裝的 \lib 子目錄。

- PATH，如果該工具必須執行 CVTRES，但在 LINK 本身的相同目錄中找不到檔案。 (LINK 要求 CVTRES 連結 .res 檔案。PATH 必須指向可視化C++安裝的 \bin 子目錄。

- TMP，在連結 OMF 或 .res 檔案時指定目錄。

## <a name="see-also"></a>另請參閱

[C/C++ 建譯參考](c-cpp-building-reference.md)
[MSVC 連結器選項](linker-options.md)
[模組定義 (.def) 檔案](module-definition-dot-def-files.md)
[連結器支援延遲載入的 DLL](linker-support-for-delay-loaded-dlls.md)
