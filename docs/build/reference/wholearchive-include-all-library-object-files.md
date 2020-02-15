---
title: /WHOLEARCHIVE （包含所有程式庫物件檔案）
ms.date: 02/12/2020
ms.assetid: ee92d12f-18af-4602-9683-d6223be62ac9
ms.openlocfilehash: 95685c9c0dfde45c42449bbcad67228a0e21b36a
ms.sourcegitcommit: 8414cd91297dea88c480e208c7b5301db9972f19
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/14/2020
ms.locfileid: "77257529"
---
# <a name="wholearchive-include-all-library-object-files"></a>/WHOLEARCHIVE （包含所有程式庫物件檔案）

強制連結器在連結的可執行檔中包含靜態程式庫中的所有物件檔案。

## <a name="syntax"></a>語法

> **/WHOLEARCHIVE**\
> **/WHOLEARCHIVE：** 連結_庫_

### <a name="arguments"></a>引數

*程式庫*\
靜態程式庫的選擇性路徑名稱。 連結器包含這個文件庫中的每個物件檔案。

## <a name="remarks"></a>備註

/WHOLEARCHIVE 選項會強制連結器包含指定靜態程式庫中的每個物件檔案，或者，如果未指定任何程式庫，則會從指定給 LINK 命令的所有靜態程式庫。 若要指定多個程式庫的/WHOLEARCHIVE 選項，您可以在連結器命令列上使用一個以上的/WHOLEARCHIVE 參數。 根據預設，連結器只會在連結的輸出中包含物件檔案，而這些檔案會在可執行檔中匯出其他物件檔案所參考的符號。 /WHOLEARCHIVE 選項會讓連結器將封存在靜態程式庫中的所有物件檔案視為在連結器命令列上個別指定。

/WHOLEARCHIVE 選項可用來重新匯出靜態程式庫中的所有符號。 這可讓您在從多個靜態程式庫建立元件時，確保包含所有的程式庫程式碼、資源和中繼資料。 如果您在建立包含匯出 Windows 執行階段元件的靜態程式庫時看到警告 LNK4264，請在將該程式庫連結至另一個元件或應用程式時，使用/WHOLEARCHIVE 選項。

/WHOLEARCHIVE 選項是在 Visual Studio 2015 Update 2 中引進。

### <a name="to-set-this-linker-option-in-visual-studio"></a>在 Visual Studio 中設定這個連結器選項

1. 開啟專案的 [屬性頁] 對話方塊。 如需詳細資料，請參閱[在 Visual Studio 中設定 C ++ 編譯器和組建屬性](../working-with-project-properties.md)。

1. 在 [設定**屬性**]、[**連結器**] 底下，選取 [**命令列**] 屬性頁。

1. 將 [/WHOLEARCHIVE] 選項新增至 [**其他選項**] 文字方塊。

## <a name="see-also"></a>另請參閱

[MSVC 連結器參考](linking.md)<br/>
[MSVC 連結器選項](linker-options.md)
