import os

def найти_файл(имя_файла, путь_к_папке):
  """
  Находит файл в папке и ее подпапках.

  Args:
    имя_файла: Имя искомого файла (с расширением).
    путь_к_папке: Путь к папке, в которой нужно искать файл.

  Returns:
    Список путей к найденным файлам или пустой список, если файл не найден.
  """
  найденные_файлы = []
  for корень, _, файлы in os.walk(путь_к_папке):
    if имя_файла in файлы:
      найденные_файлы.append(os.path.join(корень, имя_файла))
  return найденные_файлы

# Пример использования:
имя_файла = "мой_файл.txt"
путь_к_папке = "/home/user/документы"

результат = найти_файл(имя_файла, путь_к_папке)

if результат:
  print(f"Файл '{имя_файла}' найден по следующим путям:")
  for путь in результат:
    print(путь)
else:
  print(f"Файл '{имя_файла}' не найден в папке '{путь_к_папке}'")
