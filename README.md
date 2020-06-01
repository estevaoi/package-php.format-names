# FormatName-in-PHP
## Formatação de nomes me PHP para padronização no formato

A finalidade desta função é tratar um nome qualquer (nome de pessoa) e padronizá-lo, por exemplo:

1. JOSÉ NORBERTO E SILVA: José Norberto e Silva
2. ÂNTONIO sOBRInHO Dos Santos: Ântonio Sobrinho dos Santos
3. Jéssica Cunha BraGA Da Costa: Jéssica Cunha Braga da Costa

É isso aí, espero que ajude.


```PHP
function formatName($name)
{
    if (empty($name))
        return false;

    $out = '';
    $arr = explode(' ', mb_strtolower($name));

    foreach ($arr as $value) {
        if (in_array(trim($value), array("de", "da", "e", "dos", "do"))) {
            $out .= $value . ' ';
        } else {
            $out .= mb_convert_case($value, MB_CASE_TITLE, 'UTF-8') . ' ';
        }
    }

    return trim($out);
}

formatName('JOSÉ NORBERTO E SILVA');        // José Norberto e Silva
formatName('ÂNTONIO sOBRInHO Dos Santos');  // Ântonio Sobrinho dos Santos
formatName('Jéssica Cunha BraGA Da Costa'); // Jéssica Cunha Braga da Costa
```

[estevao.io](https://estevao.io)
