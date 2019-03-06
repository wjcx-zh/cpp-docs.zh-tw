---
title: /BASE (基底位址)
ms.date: 09/05/2018
f1_keywords:
- /base
- VC.Project.VCLinkerTool.BaseAddress
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
ms.openlocfilehash: 87fdceea4ac71fe4bf0a53d7ae8e473bc97a01d7
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2019
ms.locfileid: "57416744"
---
# <a name="base-base-address"></a>/BASE (基底位址)

指定程式的基底位址。

## <a name="syntax"></a>語法

> **/BASE:**{*address*[**,**<em>size</em>] | **\@**<em>filename</em>**,**<em>key</em>}

## <a name="remarks"></a>備註

> [!NOTE]
> 基於安全性理由，Microsoft 建議您使用[/DYNAMICBASE](../../build/reference/dynamicbase-use-address-space-layout-randomization.md)選項，而不要指定可執行檔基底位址。 這會產生可執行映像可以隨機重定基底在載入時使用 Windows 的位址空間配置隨機載入 (ASLR) 功能。 /DYNAMICBASE 選項預設為開啟。

/ 基底的選項會設定程式，覆寫.exe 或 DLL 檔案的預設位置的基底位址。 .Exe 檔案的預設基底位址是 32 位元映像的 0x400000 或 0x140000000 64 位元映像。 為 dll，請的預設基底位址是 0x10000000 32 位元映像或 0x180000000 64 位元映像。 在作業系統上不支援位址空間配置隨機載入 (ASLR)，或 /dynamicbase: no 選項已設定時，作業系統會先嘗試載入的方案，其指定或預設的基底位址。 如果有足夠的空間找不到可用，系統重新放置到該程式。 若要防止重新配置，請使用[/fixed](../../build/reference/fixed-fixed-base-address.md)選項。

連結器會發出錯誤，如果*地址*不是 64 K 的倍數。 您可以選擇性地指定該程式; 的大小如果程式不能配合您所指定的大小，則連結器會發出警告。

命令列上指定的基底位址的另一種方式是使用基底的位址回應檔。 基底的位址回應檔是文字檔，其中包含基底地址和選擇性的所有 Dll 會使用您的程式，以及每個基底位址的唯一文字索引鍵的大小。 若要使用回應檔案，以指定的基底位址，使用 at 符號 (**\@**) 再加上的回應檔名稱*filename*，後面接著一個逗號，則*金鑰*檔案中使用的基底地址的值。 連結器會尋找*filename*中任一個指定的路徑，或如果未指定路徑，LIB 環境變數中指定之目錄中。 中的每一行*filename*代表一個 DLL 並具有下列語法：

> *索引鍵* *地址* [*大小*] **;** *註解*

*金鑰*是英數字元的字串，不區分大小寫。 它通常是 DLL 的名稱，但不是需要。 *金鑰*後面接著基底*地址*在 C 語言、 十六進位或是十進位標記法和選擇性的最大*大小*。 所有的三個引數是以空格或定位字元分隔。 連結器會發出警告，如果指定*大小*小於程式所需的虛擬位址空間。 A*註解*指定分號 (**;**) 可以位於相同或不同的行。 連結器會忽略從分號到行結尾的所有文字。 此範例會示範這類檔案的一部分：

```
main   0x00010000    0x08000000    ; for PROJECT.exe
one    0x28000000    0x00100000    ; for DLLONE.DLL
two    0x28100000    0x00300000    ; for DLLTWO.DLL
```

如果包含這些資料行的檔案便稱為 dlls.txt 命令，下列範例命令會套用這項資訊：

```
link dlltwo.obj /dll /base:@dlls.txt,two
```

設定基底地址的另一個方法是使用*基底*中的引數[名稱](../../build/reference/name-c-cpp.md)或是[文件庫](../../build/reference/library.md)陳述式。 /BASE 並[/DLL](../../build/reference/dll-build-a-dll.md)選項一起相當於**程式庫**陳述式。

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個連結器選項

1. 開啟專案的 [屬性頁]  對話方塊。 如需詳細資訊，請參閱 <<c0> [ 設定 Visual c + + 專案屬性](../../ide/working-with-project-properties.md)。

1. 選取 **組態屬性** > **連結器** > **進階**屬性頁。

1. 修改**基底位址**屬性。

### <a name="to-set-this-linker-option-programmatically"></a>若要以程式設計方式設定這個連結器選項

- 請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.BaseAddress%2A>。

## <a name="see-also"></a>另請參閱

[設定連結器選項](../../build/reference/setting-linker-options.md)<br/>
[連結器選項](../../build/reference/linker-options.md)
