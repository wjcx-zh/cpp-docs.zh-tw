---
title: 使用 Managed 例外狀況中的基本概念
ms.date: 11/04/2016
helpviewer_keywords:
- try-catch exception handling, managed applications
- __finally keyword, managed exceptions
- exceptions, managed
- try-catch exception handling
- catch blocks
- throwing exceptions, managed exceptions
- Visual C++, handling managed exceptions
ms.assetid: 40ce8931-1ecc-491a-815f-733b23fcba35
ms.openlocfilehash: 4eeec5db00ceca5429f4a3a270e1b249a8955249
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87230918"
---
# <a name="basic-concepts-in-using-managed-exceptions"></a>使用 Managed 例外狀況中的基本概念

本主題討論 managed 應用程式中的例外狀況處理。 也就是使用 **/clr**編譯器選項編譯的應用程式。

## <a name="in-this-topic"></a>本主題內容

- [在/clr 下擲回例外狀況](#vcconbasicconceptsinusingmanagedexceptionsanchor1)

- [CLR 延伸模組的 Try/Catch 區塊](#vcconbasicconceptsinusingmanagedexceptionsanchor2)

## <a name="remarks"></a>備註

如果您使用 **/clr**選項進行編譯，則可以處理 clr 例外狀況，而標準 <xref:System.Exception> 類別則提供許多有用的方法來處理 clr 例外狀況，而且建議做為使用者定義例外狀況類別的基類。

**/Clr**不支援攔截衍生自介面的例外狀況類型。 此外，common language runtime 不允許您捕捉堆疊溢位例外狀況;堆疊溢位例外狀況會終止進程。

如需受控和未受管理的應用程式中例外狀況處理差異的詳細資訊，請參閱[Managed Extensions for C++ 之下例外狀況處理行為的差異](../dotnet/differences-in-exception-handling-behavior-under-clr.md)。

## <a name="throwing-exceptions-under-clr"></a><a name="vcconbasicconceptsinusingmanagedexceptionsanchor1"></a>在/clr 下擲回例外狀況

C + + throw 運算式已擴充，以擲回 CLR 類型的控制碼。 下列範例會建立自訂例外狀況類型，然後擲回該類型的實例：

```cpp
// clr_exception_handling.cpp
// compile with: /clr /c
ref struct MyStruct: public System::Exception {
public:
   int i;
};

void GlobalFunction() {
   MyStruct^ pMyStruct = gcnew MyStruct;
   throw pMyStruct;
}
```

實值型別必須先進行裝箱，才會擲回：

```cpp
// clr_exception_handling_2.cpp
// compile with: /clr /c
value struct MyValueStruct {
   int i;
};

void GlobalFunction() {
   MyValueStruct v = {11};
   throw (MyValueStruct ^)v;
}
```

## <a name="trycatch-blocks-for-clr-extensions"></a><a name="vcconbasicconceptsinusingmanagedexceptionsanchor2"></a>CLR 延伸模組的 Try/Catch 區塊

相同的 **`try`** / **`catch`** 區塊結構可以用來捕捉 CLR 和原生例外狀況：

```cpp
// clr_exception_handling_3.cpp
// compile with: /clr
using namespace System;
ref struct MyStruct : public Exception {
public:
   int i;
};

struct CMyClass {
public:
   double d;
};

void GlobalFunction() {
   MyStruct^ pMyStruct = gcnew MyStruct;
   pMyStruct->i = 11;
   throw pMyStruct;
}

void GlobalFunction2() {
   CMyClass c = {2.0};
   throw c;
}

int main() {
   for ( int i = 1; i >= 0; --i ) {
      try {
         if ( i == 1 )
            GlobalFunction2();
         if ( i == 0 )
            GlobalFunction();
      }
      catch ( CMyClass& catchC ) {
         Console::WriteLine( "In 'catch(CMyClass& catchC)'" );
         Console::WriteLine( catchC.d );
      }
      catch ( MyStruct^ catchException ) {
         Console::WriteLine( "In 'catch(MyStruct^ catchException)'" );
         Console::WriteLine( catchException->i );
      }
   }
}
```

### <a name="output"></a>輸出

```
In 'catch(CMyClass& catchC)'
2
In 'catch(MyStruct^ catchException)'
11
```

### <a name="order-of-unwinding-for-c-objects"></a>C + + 物件的回溯順序

具有析構函式之任何 c + + 物件的回溯會發生在擲回函數和處理函數之間的執行時間堆疊上。 因為 CLR 類型是在堆積上配置，所以回溯不適用。

所擲回例外狀況的事件順序如下所示：

1. 執行時間會引導堆疊尋找適當的 catch 子句，或在 SEH 的情況下，使用 seh 的 except 篩選準則來攔截例外狀況。 Catch 子句會先以詞法順序搜尋，然後再動態地向下呼叫堆疊。

1. 一旦找到正確的處理常式，就會將堆疊展開到該點。 對於堆疊上的每個函式呼叫，其本機物件都是解構的，而且會從大部分的對外向外執行 __finally 區塊。

1. 展開堆疊之後，就會執行 catch 子句。

### <a name="catching-unmanaged-types"></a>攔截非受控類型

當擲回非受控物件類型時，它會包裝為類型的例外狀況 <xref:System.Runtime.InteropServices.SEHException> 。 搜尋適當的子句時 **`catch`** ，有兩種可能性。

- 如果遇到原生 c + + 型別，則例外狀況會解除包裝並與所遇到的類型相比較。 這項比較可讓原生 c + + 類型以正常方式攔截。

- 不過，如果 **`catch`** 先檢查**SEHException**類型的子句或其任何基類，則子句會攔截例外狀況。 因此，您應該在 CLR 類型的任何 catch 子句之前，先放置攔截原生 c + + 類型的所有 catch 子句。

請注意

```
catch(Object^)
```

和

```
catch(...)
```

會攔截任何擲回的型別，包括 SEH 例外狀況。

如果 catch （Object ^）攔截到非受控型別，它就不會損毀所擲回的物件。

當擲回或攔截未受管理的例外狀況時，建議您使用[/ehsc](../build/reference/eh-exception-handling-model.md)編譯器選項，而不要使用 **/ehs**或 **/eha**。

## <a name="see-also"></a>另請參閱

[例外狀況處理](../extensions/exception-handling-cpp-component-extensions.md)<br/>
[safe_cast](../extensions/safe-cast-cpp-component-extensions.md)<br/>
[例外狀況處理](../cpp/exception-handling-in-visual-cpp.md)
