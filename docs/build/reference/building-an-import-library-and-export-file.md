---
title: 建置匯入程式庫和匯出檔案 |Microsoft Docs
ms.custom: ''
ms.date: 09/05/2018
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- VC.Project.VCLibrarianTool.ModuleDefinitionFile
- VC.Project.VCLibrarianTool.ExportNamedFunctions
- VC.Project.VCLibrarianTool.GenerateDebug
- VC.Project.VCLibrarianTool.ForceSymbolReferences
dev_langs:
- C++
helpviewer_keywords:
- OUT library manager option
- INCLUDE library manager option
- /DEF library manager option
- exporting data
- import libraries, building
- -INCLUDE library manager option
- /OUT library manager option
- DEF library manager option
- -DEF library manager option
- -OUT library manager option
- /INCLUDE library manager option
- -EXPORT library manager option
- exporting data, export (.exp) files
- /EXPORT library manager option
- EXPORT library manager option
- .lib files
- EXP files
ms.assetid: 2fe4f30a-1dd6-4b05-84b5-0752e1dee354
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 75f629c8a9c8a06f02024e9d52ab13b2d12b234c
ms.sourcegitcommit: 997e6b7d336cddb388bb6e9e56527725fcaa0624
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/08/2018
ms.locfileid: "48860383"
---
# <a name="building-an-import-library-and-export-file"></a>建置匯入程式庫和匯出檔案

若要建置匯入程式庫和匯出檔案，使用下列語法：

> **LIB /DEF**[**:**<em>deffile</em>] [*選項*] [*objfiles*] [*程式庫*]

/DEF 指定時，程式庫會從 LIB 命令中傳遞的匯出規格建立的輸出檔。 有三種方法來指定匯出，建議使用的順序中所列：

1. A **__declspec （dllexport)** 其中一種定義*objfiles*或*程式庫*

1. /EXPORT 規格：*名稱*LIB 命令列上

1. 中的定義**匯出**中的陳述式*deffile*

這些是您用來連結匯出的程式時，指定匯出的相同方法。 程式可以使用一個以上的方法。 您可以指定組件的 LIB 命令 (例如多個*objfiles*或 /EXPORT 規格) 在 LIB 命令中的命令檔，就如同您可以在 [連結] 命令。

下列選項會套用至建置匯入程式庫和匯出檔案：

> **/ OUT:** *匯入*

覆寫預設的輸出檔案名稱，如*匯入*所建立的程式庫。 /OUT 未指定，預設的名稱時，第一個物件檔案或程式庫中的 LIB 命令和擴充功能的基底名稱。 lib。 匯出檔案會提供相同的基底名稱做為匯入程式庫和擴充功能。 exp。

> **/Export:** *entryname* \[ **=** *internalname*]\[，**\@**<em>序數</em>\[， **NONAME**]]\[，**資料**]

匯出函式，從您的程式，以允許其他程式以呼叫函式。 您也可以匯出資料 (使用**資料**關鍵字)。 匯出通常是在 DLL 中定義。

*Entryname*是函式或資料的項目名稱，因為它是可供呼叫端程式。 您可以選擇性地指定*internalname*當做函式定義的程式中，根據預設，已知*internalname*等同於*entryname*。 *序數*範圍 1 到 65535 之間的匯出資料表指定的索引，如果您未指定*序數*，LIB 指派其中一個。 **NONAME**關鍵字匯出函式只能做為序數，而不*entryname*。 **資料**關鍵字用來匯出只有資料的物件。

> **/INCLUDE:** *符號*

將指定*符號*至符號表。 此選項可用於強制使用程式庫物件，否則不會包含項目。

請注意，是否您建立您匯入程式庫中第一步，建立.dll 之前，您必須傳遞同一組物件檔案建置.dll 時為您成功建置匯入程式庫時。

## <a name="see-also"></a>另請參閱

[與匯入程式庫和匯出檔案一起使用](../../build/reference/working-with-import-libraries-and-export-files.md)
