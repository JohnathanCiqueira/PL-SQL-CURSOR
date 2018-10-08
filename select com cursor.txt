DECLARE
    v_id cliente.id%type;
    v_segmercado_id cliente.segmercado_id%type := 1;
    CURSOR cur_cliente is
            SELECT id
            FROM cliente;
BEGIN
    OPEN cur_cliente;    
    LOOP
        FETCH cur_cliente into v_id;
        EXIT WHEN cur_cliente%NOTFOUND;
        ATUALIZAR_CLI_SEG_MERCADO(v_id, v_segmercado_id);
    END LOOP;
    
    CLOSE cur_cliente;
    
    COMMIT;
END;

select * from cliente;