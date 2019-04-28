---
title: /WHOLEARCHIVE （包括所有的程式庫目的檔）
ms.date: 11/04/2016
ms.assetid: ee92d12f-18af-4602-9683-d6223be62ac9
ms.openlocfilehash: db99816b18110b424647603196040997044e7fbd
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62316427"
---
# <a name="wholearchive-include-all-library-object-files"></a>/WHOLEARCHIVE （包括所有的程式庫目的檔）

Force 連結器在連結的可執行檔中的靜態程式庫中包含物件的所有檔案。

## <a name="syntax"></a>語法

> /WHOLEARCHIVE[:*library*]

## <a name="remarks"></a>備註

已將 /WHOLEARCHIVE 選項會強制連結器，以包含每個物件檔案，從指定的靜態程式庫，或如果未不指定任何程式庫，從指定至連結的所有靜態程式庫的命令。 若要指定多個程式庫的已將 /WHOLEARCHIVE 選項，您可以在連結器命令列上使用一個以上已將 /WHOLEARCHIVE 切換。 根據預設，連結器包含物件中檔案連結的輸出這些匯出參考其他物件中的檔案可執行檔的符號時，才。 已將 /WHOLEARCHIVE 選項可讓連結器將封存的靜態程式庫，如同個別指定連結器命令列上的所有目的檔。

已將 /WHOLEARCHIVE 選項可用來重新匯出從靜態程式庫的所有符號。 這可讓您確保所有您的程式庫程式碼、 資源和中繼資料都包含一個以上的靜態程式庫從建立元件時。 如果您看到警告 LNK4264，當您建立靜態程式庫，包含匯出的 Windows 執行階段元件，請將該程式庫連結到另一個元件或應用程式時使用已將 /WHOLEARCHIVE 選項。

已將 /WHOLEARCHIVE 選項已引入 Visual Studio 2015 Update 2。

### <a name="to-set-this-linker-option-in-visual-studio"></a>在 Visual Studio 中設定這個連結器選項

1. 開啟專案的 [ **屬性頁** ] 對話方塊。 如需詳細資訊，請參閱 <<c0> [ 設定C++Visual Studio 中的編譯器和組建屬性](../working-with-project-properties.md)。</c0>

1. 選取 **命令列**下方的 屬性頁**組態屬性**，**連結器**。

1. 新增已將 /WHOLEARCHIVE 選項，以**其他選項**文字方塊。

## <a name="see-also"></a>另請參閱

[MSVC 連結器參考](linking.md)<br/>
[MSVC 連結器選項](linker-options.md)
