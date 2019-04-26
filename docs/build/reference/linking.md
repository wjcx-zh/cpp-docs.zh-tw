---
title: MSVC 連結器參考
ms.date: 12/10/2018
ms.assetid: bb736587-d13b-4f3c-8982-3cc2c015c59c
ms.openlocfilehash: 3a9eebef0a264b0131311b5ca96011a4d56264a1
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62176625"
---
# <a name="linking"></a>連結

在C++專案中，*連結*編譯器已編譯的原始程式碼到物件檔案 (*.obj) 之後，會執行步驟。 連結器 (link.exe) 會將物件檔案結合成單一的可執行檔。 

內部或外部 Visual Studio，可以設定連結器選項。 在 Visual Studio 中，您必須存取連結器選項中的專案節點上按一下滑鼠右鍵**方案總管**，然後選擇**屬性**來顯示屬性頁。 選擇**連結器**展開節點，並查看所有選項的左窗格中。 


## <a name="linker-command-line-syntax"></a>連結器命令列語法

當您執行 Visual Studio 外部的連結時，您可以指定輸入一或多個方式：

- 在命令列上

- 使用命令檔

- 在 環境變數

第一個程序選項連結連結環境變數中指定，後面接著在命令列指定的順序和命令檔中的選項。 如果使用不同的引數重複選項時，最後一個處理的優先順序較高。

選項會套用至整個建置;沒有選項可以套用至特定的輸入檔中。

若要執行連結。EXE，使用下列命令語法：

```
LINK arguments
```

`arguments`包含選項和檔名，而且可以依任何順序指定。 選項為已處理的第一個，則檔案。 使用一或多個空格或定位點分隔的引數。

> [!NOTE]
>  您可以啟動此工具只能從 Visual Studio 命令提示字元。 您無法從系統命令提示字元，或從 [檔案總管] 啟動它。

## <a name="command-line"></a>命令列

命令列選項選項規範組成，破折號 （-） 或斜線 （/），後面接著選項的名稱。 選項名稱不能被縮寫。 有些選項需要引數，指定在冒號 （:） 之後。 沒有空格或定位字元內允許的選項規格中，除了 /COMMENT 選項中加上引號的字串內。 以十進位數或 C 語言標記法指定數字的引數。 選項名稱和其關鍵字或檔名引數不區分大小寫，但做為引數的識別碼會區分大小寫。

若要傳送檔案至連結器，請在命令列上指定檔案名稱之後連結 命令。 您可以指定絕對或相對路徑與檔名，以及您可以使用萬用字元在檔名。 如果您省略的點 （.） 和檔案名稱副檔名，連結會假設為了尋找檔案的.obj。 連結不會使用副檔名或缺乏將內容假設檔案，它會藉由檢查，判斷檔案類型，並加以處理。

link.exe 會傳回成功 （沒有錯誤） 的零。  否則，連結器會傳回停止連結的錯誤號碼。  例如，如果連結器產生 LNK1104，連結器就會傳回 1104年。  因此，連結器發生錯誤時傳回的最低錯誤編號為 1000年。  傳回值 128 代表作業系統或.config 檔案; 的組態問題載入器未載入 link.exe 或 c2.dll。

## <a name="link-command-files"></a>LINK 命令檔

您可以將命令列引數傳遞的命令檔形式的連結。 若要指定連結器的命令檔，請使用下列語法：

> **連結\@**  <em>commandfile&lt</em>

*Commandfile&lt*是文字檔案的名稱。 允許之間沒有空格或定位字元 at 符號 (**\@**) 和檔案名稱。 沒有任何預設的延伸模組;您必須指定完整的檔名，包括任何副檔名。 無法使用萬用字元。 您可以指定絕對或相對路徑與檔案名稱。 連結不會使用環境變數來搜尋此檔案。

在命令檔中，引數可以分隔的空格或定位字元 （因為在命令列上） 和新行字元。

您可以指定全部或部分命令列中的命令檔。 您可以使用多個 LINK 命令中的命令檔。 連結會接受命令檔案輸入，如同它已指定命令列上該位置中。 不可為巢狀命令檔。 連結回應命令檔案的內容，除非[/NOLOGO](nologo-suppress-startup-banner-linker.md)指定選項。

## <a name="example"></a>範例

下列命令以建置 DLL 會傳入不同的命令檔中的物件檔案和程式庫的名稱，並會使用第三個命令的 /EXPORTS 選項指定的檔案：

```cmd
link /dll @objlist.txt @liblist.txt @exports.txt
```

## <a name="link-environment-variables"></a>LINK 環境變數

LINK 工具使用下列環境變數：

- 連結和\_連結\_，如果已定義。 [連結] 工具前面加上 LINK 環境變數中定義的引數選項和，並附加選項和引數中定義\_連結\_環境變數，以處理前的命令列引數。

- LIB (若已定義)。 搜尋物件、 程式庫或在命令列上或藉由指定其他檔案時，LINK 工具會使用 LIB 路徑[基底/](base-base-address.md)選項。 它也會使用 LIB 路徑來尋找物件中指定的 .pdb 檔案。 LIB 變數可以包含一或多個以分號分隔的路徑規格。 一個路徑必須指向 Visual C++ 安裝的 \lib 子目錄。

- PATH，如果該工具必須執行 CVTRES，但在 LINK 本身的相同目錄中找不到檔案。 (LINK 需要 CVTRES 才能連結 .res 檔案。)PATH 必須指向 Visual C++ 安裝的 \bin 子目錄。

- TMP，在連結 OMF 或 .res 檔案時指定目錄。

## <a name="see-also"></a>另請參閱

[C /C++建置參考](c-cpp-building-reference.md)
[MSVC 連結器選項](linker-options.md)
[模組定義 (.def) 檔](module-definition-dot-def-files.md)
[連結器支援適用於延遲載入 Dll](linker-support-for-delay-loaded-dlls.md)
