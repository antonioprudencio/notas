# notas odoo


```sql
-- seleciona id_texto por id numerico do menu
SELECT m.id, m.name, d.module, d.name AS xml_name
FROM ir_ui_menu m
JOIN ir_model_data d ON d.model = 'ir.ui.menu' AND d.res_id = m.id
WHERE m.id = 193;
```

```sql
-- seleciona id_externo por id numerico por id da action
SELECT
    imd.module || '.' || imd.name AS external_id,
    ia.id,
    ia.name
FROM
    ir_model_data imd
JOIN
    ir_actions ia ON ia.id = imd.res_id
WHERE
    imd.model = 'ir.actions.act_window'
    AND ia.id = 434;
```
