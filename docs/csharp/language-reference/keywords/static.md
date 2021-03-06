---
title: "static (C# リファレンス)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- static
- static_CSharpKeyword
dev_langs:
- CSharp
helpviewer_keywords:
- static keyword [C#]
ms.assetid: 5509e215-2183-4da3-bab4-6b7e607a4fdf
caps.latest.revision: 26
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 8e46dc2f00d1c185379dba1017ca445b9ae5ae72
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="static-c-reference"></a>static (C# リファレンス)
`static` 修飾子は、静的メンバーの宣言に使用します。静的メンバーは、特定のオブジェクトではなく、型自体に属するメンバーです。 `static` 修飾子は、クラス、フィールド、メソッド、プロパティ、演算子、イベント、コンストラクターと組み合わせて使用できますが、クラス以外のインデクサー、ファイナライザー、型で使うことはできません。 詳細については、「[静的クラスと静的クラス メンバー](../../../csharp/programming-guide/classes-and-structs/static-classes-and-static-class-members.md)」を参照してください。  
  
## <a name="example"></a>例  
 次のクラスは `static` として宣言され、`static` メソッドのみが含まれます。  
  
 [!code-cs[csrefKeywordsModifiers#18](../../../csharp/language-reference/keywords/codesnippet/CSharp/static_1.cs)]  
  
 定数宣言や型宣言は、暗黙的な静的メンバーです。  
  
 静的メンバーは、インスタンスを使って参照できません。 代わりに、型の名前を使って参照します。 たとえば、次のクラスを考えます。  
  
 [!code-cs[csrefKeywordsModifiers#19](../../../csharp/language-reference/keywords/codesnippet/CSharp/static_2.cs)]  
  
 静的メンバー `x` を参照するには、同じスコープからその静的メンバーにアクセス可能でない限り、完全修飾名 (`MyBaseC.MyStruct.x`) を使用します。  
  
```csharp  
Console.WriteLine(MyBaseC.MyStruct.x);  
```  
  
 クラスのインスタンスには、そのクラスのインスタンス フィールドすべてにそれぞれのコピーが含まれていますが、各静的フィールドのコピーは 1 つだけです。  
  
 静的メソッドまたはプロパティ アクセサーへの参照には、[this](../../../csharp/language-reference/keywords/this.md) は使用できません。  
  
 `static` キーワードをクラスに適用する場合、そのクラスのすべてのメンバーが静的でなければなりません。  
  
 クラスおよび静的クラスには、静的コンストラクターを含めることができます。 静的コンストラクターは、プログラムが開始されてからクラスがインスタンス化されるまでの間に呼び出されます。  
  
> [!NOTE]
>  `static` キーワードの用法は、C++ の場合よりも制限されています。 C++ キーワードと比較するには、「[ストレージ クラス (C++)](/cpp/cpp/storage-classes-cpp#static)」をご覧ください。
  
 静的メンバーの例を示すために、ある企業の従業員を表すクラスを考えてみます。 このクラスには、従業員数を数えるメソッドと、従業員数を格納するフィールドがあります。 メソッドとフィールドはどちらも、従業員のインスタンスに属しておらず、 企業クラスに属しています。 そのため、クラスの静的メンバーとして宣言する必要があります。  
  
## <a name="example"></a>例  
 この例では、新しい従業員の名前と ID を読み取り、従業員数のカウンターを 1 つインクリメントして、新しい従業員の情報と従業員数を表示します。 説明を簡単にするために、この例では、現在の従業員数をキーボード入力から読み取っていますが、 実際のアプリケーションでは、ファイルから情報を読み取るようにしてください。  
  
 [!code-cs[csrefKeywordsModifiers#20](../../../csharp/language-reference/keywords/codesnippet/CSharp/static_3.cs)]  
  
## <a name="example"></a>例  
 この例では、宣言されていない別の静的フィールドを使用して静的フィールドを初期化できても、静的フィールドに値を明示的に割り当てない限り、結果は未定義になることを示します。  
  
 [!code-cs[csrefKeywordsModifiers#21](../../../csharp/language-reference/keywords/codesnippet/CSharp/static_4.cs)]  
  
## <a name="c-language-specification"></a>C# 言語仕様  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [C# リファレンス](../../../csharp/language-reference/index.md)   
 [C# プログラミング ガイド](../../../csharp/programming-guide/index.md)   
 [C# のキーワード](../../../csharp/language-reference/keywords/index.md)   
 [修飾子](../../../csharp/language-reference/keywords/modifiers.md)   
 [静的クラスと静的クラス メンバー](../../../csharp/programming-guide/classes-and-structs/static-classes-and-static-class-members.md)

