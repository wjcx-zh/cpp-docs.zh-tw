---
title: -c （編譯而不連結） |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /c
dev_langs:
- C++
helpviewer_keywords:
- suppress link
- cl.exe compiler, compiling without linking
- -c compiler option [C++]
- c compiler option [C++]
- /c compiler option [C++]
ms.assetid: 8017fc3d-e5dd-4668-a1f7-3120daa95d20
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: de6fe291bde8652b772c7091c1919836f88960fd
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/17/2018
ms.locfileid: "45710342"
---
# <a name="c-compile-without-linking"></a>/c (編譯而不連結)

可防止連結自動呼叫。

## <a name="syntax"></a>語法

```
/c
```

## <a name="remarks"></a>備註

在以編譯 **/c**建立僅限.obj 檔案。 您必須明確呼叫連結，使用適當的檔案和執行組建的 「 連結 」 階段的選項。

在開發環境中建立的任何內部專案會使用 **/c**預設選項。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個編譯器選項

- 無法從開發環境內使用此選項。

### <a name="to-set-this-compiler-option-programmatically"></a>若要以程式方式設定這個編譯器選項

- 若要以程式設計方式設定這個編譯器選項，請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.CompileOnly%2A>。

## <a name="example"></a>範例

下列命令列建立 FIRST.obj 和 SECOND.obj 物件檔案。THIRD.obj 會被忽略。

```
CL /c FIRST.C SECOND.C THIRD.OBJ
```

若要建立可執行檔，您必須叫用連結：

```
LINK firsti.obj second.obj third.obj /OUT:filename.exe
```

## <a name="see-also"></a>另請參閱

[編譯器選項](../../build/reference/compiler-options.md)<br/>
[設定編譯器選項](../../build/reference/setting-compiler-options.md)