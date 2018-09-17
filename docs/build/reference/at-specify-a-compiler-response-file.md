---
title: '@ （指定編譯器回應檔） |Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- '@'
dev_langs:
- C++
helpviewer_keywords:
- response files, C/C++ compiler
- '@ compiler option'
- cl.exe compiler, specifying response files
ms.assetid: 400fffee-909d-4f60-bf76-45833e822685
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 9c86d49aea2ce7a8d8b438c64cd883b71e5a4646
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/17/2018
ms.locfileid: "45720846"
---
# <a name="-specify-a-compiler-response-file"></a>@ (指定編譯器回應檔)

指定編譯器回應檔。

## <a name="syntax"></a>語法

> **\@**<em>response_file</em>

## <a name="arguments"></a>引數

*response_file*<br/>
包含編譯器命令的文字檔。

## <a name="remarks"></a>備註

回應檔案可以包含您可以在命令列指定的任何命令。 如果您的命令列引數超過 127 個字元，這會很有用。

您不能指定**\@** 選項回應檔內。 也就是說，回應檔無法內嵌其他回應檔案。

從命令列中，您可以指定多個回應檔選項 (例如`@respfile.1 @respfile.2`) 您的需要。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個編譯器選項

- 回應檔不能在開發環境中從指定，而且必須在命令列指定。

### <a name="to-set-this-compiler-option-programmatically"></a>若要以程式方式設定這個編譯器選項

- 這個編譯器選項不能以程式設計方式變更。

## <a name="see-also"></a>另請參閱

[編譯器選項](../../build/reference/compiler-options.md)<br/>
[設定編譯器選項](../../build/reference/setting-compiler-options.md)
