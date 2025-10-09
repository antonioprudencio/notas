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

Adiciona acao no botao de action


    <record id="action_criar_usuario" model="ir.actions.server">
        <field name="name">Criar Usuário</field>
        <field name="model_id" ref="base.model_res_partner"/>
        <field name="state">code</field>
        <field name="code">
            record.action_criar_usuario()
        </field>
    </record>

    <!-- Adicionando ao menu "Ação" -->
   <record id="action_criar_usuario_ir" model="ir.actions.server">
    <field name="name">Criar Usuário</field>
    <field name="model_id" ref="base.model_res_partner"/>
    <field name="state">code</field>
    <field name="code">
        record.action_criar_usuario()
    </field>
    <field name="binding_model_id" ref="base.model_res_partner"/>
</record>


Customiza view da wizard
<form string="Titulo" class="o_form_full_width">
        <sheet>
          <div style="min-height: 150px; display: flex; align-items: center; justify-content: center;">
            <field name="mensagem" readonly="1" nolabel="1"
                   style="white-space: pre-line; width: 100%; height: 100%; font-size: 15px; text-align: center;"/>
          </div>
        </sheet>
        <footer>
          <button name="action_confirmar" string="CONFIRMAR" type="object" class="btn-primary"/>
          <button string="CANCELAR" class="btn-secondary" special="cancel"/>
        </footer>
      </form>
