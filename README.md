# Kogane System.Text.Json

Unity で System.Text.Json を使えるようにするだけのパッケージ  
Unity 2021.2.7f1 で動作確認済み

## 使用例

```cs
using System.Text.Encodings.Web;
using System.Text.Json;
using UnityEngine;

public sealed class Character
{
    public int    Id   { get; set; }
    public string Name { get; set; }
}

public class Example : MonoBehaviour
{
    private void Start()
    {
        var characters = new Character[]
        {
            new() { Id = 1, Name = "フシギダネ" },
            new() { Id = 2, Name = "フシギソウ" },
            new() { Id = 3, Name = "フシギバナ" },
        };

        var options = new JsonSerializerOptions
        {
            Encoder       = JavaScriptEncoder.UnsafeRelaxedJsonEscaping,
            WriteIndented = true,
        };

        var json = JsonSerializer.Serialize( characters, options );

        Debug.Log( json );
    }
}
```