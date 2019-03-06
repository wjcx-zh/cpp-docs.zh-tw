---
title: /ORDER (依順序置放函式)
ms.date: 09/05/2018
f1_keywords:
- VC.Project.VCLinkerTool.FunctionOrder
- /order
helpviewer_keywords:
- ORDER linker option
- -ORDER linker option
- LINK tool [C++], program optimizing
- /ORDER linker option
- LINK tool [C++], swap tuning
- paging, optimizing
ms.assetid: ecf5eb3e-e404-4e86-9a91-4e5ec157261a
ms.openlocfilehash: 5429876d9bfae7d8b317d52d69f0b21c720b002a
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2019
ms.locfileid: "57418070"
---
# <a name="order-put-functions-in-order"></a>/ORDER (依順序置放函式)

指定連結的順序 (COMDAT) 的個別封裝函式。

## <a name="syntax"></a>語法

> **/ORDER:\@**<em>檔名</em>

### <a name="parameters"></a>參數

*filename*<br/>
指定 COMDAT 函式的連結順序的文字檔。

## <a name="remarks"></a>備註

**/Order**編譯器選項可讓您群組以及它所呼叫之函式的函式，以最佳化您的程式分頁行為。 您也可以將經常呼叫的函式群組在一起。 這些技術，稱為*交換微調*或是*分頁最佳化*，增加機率的需要不需要從磁碟中分頁時，呼叫的函式是在記憶體中。

當您編譯您的程式碼到物件的檔案時，您可以指示編譯器將每個函式放入自己的區段，稱為*COMDAT*，利用[/Gy （啟用函式階層連結）](../../build/reference/gy-enable-function-level-linking.md)編譯器選項。 **/Order**連結器選項會告訴連結器將 Comdat 放入可執行映像，您所指定的順序。

若要指定 COMDAT 順序，請建立*回應檔案*，依名稱，其中每一行，您想要連結器要放置它們的順序列出每個 COMDAT 的文字檔。 此檔案名稱傳遞給*檔名*參數 **/** 選項。 對 c + + 函式的 COMDAT，名稱會是裝飾的形式的函式名稱。 使用 C 函式的未裝飾的名稱`main`，，在 c + + 函式宣告為`extern "C"`。 函式名稱和裝飾的名稱是區分大小寫。 如需有關裝飾名稱的詳細資訊，請參閱[裝飾名稱](../../build/reference/decorated-names.md)。

若要尋找您的 Comdat 裝飾的名稱，請使用[DUMPBIN](../../build/reference/dumpbin-reference.md)工具的[/ 符號](../../build/reference/symbols.md)物件檔案的選項。 連結器自動前面加上底線 (**\_**) 函式名稱，以回應檔案，除非名稱開頭加上問號 (**？**) 或 at 符號 ( **\@**). 例如，如果原始程式檔，example.cpp，包含函式`int cpp_func(int)`，`extern "C" int c_func(int)`並`int main(void)`，命令`DUMPBIN /SYMBOLS example.obj`列出這些裝飾的名稱：

```Output
...
088 00000000 SECT1A notype ()    External     | ?cpp_func@@YAHH@Z (int __cdecl cpp_func(int))
089 00000000 SECT22 notype ()    External     | _c_func
08A 00000000 SECT24 notype ()    External     | _main
...
```

在此案例中，指定做為名稱`?cpp_func@@YAHH@Z`， `c_func`，和`main`回應檔案中。

如果有一個以上 **/order**選項會出現在 連結器選項，指定的最後一個會生效。

**/Order**選項會停用累加連結。 您可能會看到連結器警告[LNK4075](../../error-messages/tool-errors/linker-tools-warning-lnk4075.md)當您指定這個選項已啟用累加連結，則您已指定[/ZI (增量 PDB)](../../build/reference/z7-zi-zi-debug-information-format.md)編譯器選項。 Play 這個警告，您可以使用[/incremental: no](../../build/reference/incremental-link-incrementally.md)以關閉累加連結，並使用連結器選項[/Zi (產生 PDB)](../../build/reference/z7-zi-zi-debug-information-format.md)沒有累加連結中產生 PDB 編譯器選項。

> [!NOTE]
> 連結的靜態函式無法排序，因為靜態函式名稱不是公用的符號名稱。 當 **/order**指定，則連結器警告[LNK4037](../../error-messages/tool-errors/linker-tools-warning-lnk4037.md)產生靜態或找不到順序回應檔中的每個符號。

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個連結器選項

1. 開啟專案的 [屬性頁]  對話方塊。 如需詳細資訊，請參閱 <<c0> [ 設定 Visual c + + 專案屬性](../../ide/working-with-project-properties.md)。

1. 選取 **組態屬性** > **連結器** > **最佳化**屬性頁。

1. 修改**函式順序**內容包含回應檔案的名稱。

### <a name="to-set-this-linker-option-programmatically"></a>若要以程式設計方式設定這個連結器選項

- 請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.FunctionOrder%2A>。

## <a name="see-also"></a>另請參閱

[設定連結器選項](../../build/reference/setting-linker-options.md)<br/>
[連結器選項](../../build/reference/linker-options.md)
