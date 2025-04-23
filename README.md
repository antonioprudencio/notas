# notas odoo

-- seleciona id_externo por id numerico
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
