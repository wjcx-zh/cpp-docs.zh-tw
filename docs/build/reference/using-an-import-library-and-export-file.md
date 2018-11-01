---
title: 使用匯入程式庫和匯出檔案
ms.date: 11/04/2016
helpviewer_keywords:
- circular exports
- import libraries, using
- export files
ms.assetid: 2634256a-8aa5-4495-8c9e-6cde10e4ed76
ms.openlocfilehash: e23b729bdca102ec24c4426e9784e3aab267bff2
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50484944"
---
# <a name="using-an-import-library-and-export-file"></a>使用匯入程式庫和匯出檔案

當程式 （可執行檔或 DLL） 將匯出到另一個程式，它也會匯入，或如果兩個以上的程式來匯出和匯入到彼此，連結這些程式的命令必須配合循環匯出。

在沒有循環匯出的情況下，當連結使用的程式，從另一個程式，將匯出您必須指定匯出程式匯入程式庫。 當您連結該匯出的程式，會建立匯出程式匯入程式庫。 因此，您必須連結之前匯入程式匯出的程式。 例如，如果 TWO.dll 匯入從 ONE.dll 時，您必須先將連結 ONE.dll 並取得匯入程式庫 ONE.lib。 然後，您指定 ONE.lib 連結 TWO.dll 時。 當連結器建立 TWO.dll 時，它也會建立其匯入程式庫，TWO.lib。 當連結從 TWO.dll 匯入的程式時，請使用 TWO.lib。

不過，在循環匯出的情況下，不可能全部互相依存的程式使用來自其他程式匯入程式庫的連結。 在範例中，如果 TWO.dll 也會匯出 ONE.dll、 TWO.dll 匯入程式庫不存在時連結 ONE.dll 稍早所討論。 循環匯出存在時，您必須使用程式庫來建立匯入程式庫和匯出檔案的其中一個程式。

若要開始，選擇其中一個要執行程式庫的程式。 在 [LIB] 命令，列出所有的物件和程式的程式庫，並指定 /def。 如果程式使用.def 檔或 /EXPORT 規格，以及指定這些指定。

建立匯入程式庫 (.lib) 和程式的匯出檔案 (.exp) 之後，您使用匯入程式庫，連結的其他程式時也一樣。 連結會建立每個匯出的程式，它會建置匯入程式庫。 例如，如果您執行 LIB 物件和匯出 ONE.dll，您建立 ONE.lib 和 ONE.exp。連結 TWO.dll; 時，您可以現在使用 ONE.lib此步驟也會建立匯入程式庫 TWO.lib。

最後，將您一開始有程式的連結。 在 [連結] 命令中，指定物件和程式、 程式庫建立的程式，並匯入程式庫的.exp 檔案的程式庫或程式所使用之匯出的程式庫。 若要繼續此範例，ONE.dll [連結] 命令會包含 ONE.exp 和 TWO.lib，以及物件，以及進入 ONE.dll 的程式庫。 未指定.def 檔或 /EXPORT 規格中連結命令這些不是需要，因為.exp 檔中包含的匯出定義。 當您使用.exp 檔，連結不會建立匯入程式庫，因為它會假設該.exp 檔案建立時建立。

## <a name="see-also"></a>另請參閱

[與匯入程式庫和匯出檔案一起使用](../../build/reference/working-with-import-libraries-and-export-files.md)