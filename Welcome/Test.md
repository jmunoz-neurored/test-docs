# Test

<https://www.getoutline.com/>


:::info
Prueba Info

:::


:::success
Prueba Success

:::


:::warning
Prueba Warning

:::


:::tip
Prueba Suggest

:::


`Webhook test `

> Prueba de subrayados:

 subrayado A

subrayado B

**Antiguo documento**. *¿Funcionará?* ~~¿O no funcionará?~~

```python

def count_lines(file_path):
    try:
        with open(file_path, 'r') as f:
            lines = f.readlines()
            return len(lines)
    except FileNotFoundError:
        print(f"The file '{file_path}' was not found.")
        return 0

# Script usage
file_path = 'example.txt'
total_lines = count_lines(file_path)
print(f"The file has {total_lines} lines.")
```