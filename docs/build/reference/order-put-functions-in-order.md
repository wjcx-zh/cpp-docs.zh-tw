---
title: -順序 （依順序置放函式） |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- VC.Project.VCLinkerTool.FunctionOrder
- /order
dev_langs:
- C++
helpviewer_keywords:
- ORDER linker option
- -ORDER linker option
- LINK tool [C++], program optimizing
- /ORDER linker option
- LINK tool [C++], swap tuning
- paging, optimizing
ms.assetid: ecf5eb3e-e404-4e86-9a91-4e5ec157261a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: de9b0fb629a1bf984929ec170f05e25e740e9cd5
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32378479"
---
# <a name="order-put-functions-in-order"></a>/ORDER (依順序置放函式)

指定個別封裝 (COMDAT) 函式的連結順序。

## <a name="syntax"></a>語法

>/ 排序: @*檔名*

### <a name="parameters"></a>參數

*filename*  
指定 COMDAT 函式的連結順序的文字檔。

## <a name="remarks"></a>備註

**/** 編譯器選項可讓您將分組，以及它所呼叫之函式的函式最佳化程式的分頁行為。 您也可以將經常被呼叫函式群組在一起。 這些技術，又稱為*交換微調*或*分頁最佳化*，增加了在需要時，不需要從磁碟分頁時，呼叫的函式是在記憶體中的機率。

當您編譯您的程式碼到物件的檔案時，您可以分辨每個函式放在它自己的區段，稱為編譯器*COMDAT*，使用[/Gy （啟用函式階層連結）](../../build/reference/gy-enable-function-level-linking.md)編譯器選項。 **/** 連結器選項會告訴連結器將 Comdat 放入可執行映像，您所指定的順序。

若要指定 COMDAT 順序，請建立*回應檔*，依名稱，每一行，連結器放入上的順序列出每個衝突的文字檔。 傳遞做為此檔案的名稱*filename*參數 **/** 選項。 對於 c + + 函式的 COMDAT 名稱會是函式名稱的裝飾的形式。 使用未裝飾的名稱對於 C 函式， `main`，對於 c + + 函式宣告為`extern "C"`。 函式名稱和裝飾的名稱會區分大小寫。 如需有關裝飾名稱的詳細資訊，請參閱[裝飾名稱](../../build/reference/decorated-names.md)。 

若要尋找您 Comdat 裝飾的名稱，請使用[DUMPBIN](../../build/reference/dumpbin-reference.md)工具的[/ 符號](../../build/reference/symbols.md)物件檔案上的選項。 連結器會自動前面加上底線 (\_) 至函式名稱，以回應檔案除非名稱開頭加上問號 （？） 或 at 符號 (@)。 例如，如果原始程式檔 example.cpp，包含函數`int cpp_func(int)`，`extern "C" int c_func(int)`和`int main(void)`，命令`DUMPBIN /SYMBOLS example.obj`列出這些裝飾的名稱：

```Output
...
088 00000000 SECT1A notype ()    External     | ?cpp_func@@YAHH@Z (int __cdecl cpp_func(int))
089 00000000 SECT22 notype ()    External     | _c_func
08A 00000000 SECT24 notype ()    External     | _main
...
```

在此情況下，指定做為名稱`?cpp_func@@YAHH@Z`， `c_func`，和`main`回應檔中。

如果有一個以上 **/** 選項出現在連結器選項，指定的最後一個會生效。

**/** 選項會停用累加連結。 您可能會看到連結器警告[LNK4075](../../error-messages/tool-errors/linker-tools-warning-lnk4075.md)當您指定這個選項或如果已啟用累加連結，如果您已經指定[/ZI (累加 PDB)](../../build/reference/z7-zi-zi-debug-information-format.md)編譯器選項。 這個警告轉為無回應，您可以使用[/incremental: no](../../build/reference/incremental-link-incrementally.md)連結器選項關閉累加連結，並使用[/Zi (產生 PDB)](../../build/reference/z7-zi-zi-debug-information-format.md)沒有累加連結產生 PDB 編譯器選項。

> [!NOTE]
> 連結的靜態函式無法排序，因為靜態函式名稱不是公用的符號名稱。 當 **/** 指定，則連結器警告[LNK4037](../../error-messages/tool-errors/linker-tools-warning-lnk4037.md)產生靜態或找不到順序回應檔案中的每個符號。

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個連結器選項

1. 開啟專案的 [屬性頁]  對話方塊。 如需詳細資訊，請參閱[設定 Visual c + + 專案屬性](../../ide/working-with-project-properties.md)。  

1. 在下**組態屬性**，開啟**連結器**，然後選擇 **最佳化**屬性頁。

1. 修改**函式順序**內容包含回應檔案的名稱。

### <a name="to-set-this-linker-option-programmatically"></a>若要以程式設計方式設定這個連結器選項

- 請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.FunctionOrder%2A>。

## <a name="see-also"></a>另請參閱

[設定連結器選項](../../build/reference/setting-linker-options.md)  
[連結器選項](../../build/reference/linker-options.md)