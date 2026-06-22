library IEEE;
use IEEE.STD_LOGIC_1164.ALL;

entity Detector_Secuencia is
    Port (
        clk   : in  STD_LOGIC;
        reset : in  STD_LOGIC;
        X     : in  STD_LOGIC;
        Z     : out STD_LOGIC;
		  debug_state : out std_logic_vector(2 downto 0)
    );
end Detector_Secuencia;

architecture Behavioral of Detector_Secuencia is
    -- Declaración de los estados para detectar 1011010
    type state_type is (S0, S1, S2, S3, S4, S5, S6, S7);
    signal current_state, next_state : state_type;
	 -- Esta línea obliga a Quartus a mantener la señal visible:

begin

    -- Proceso secuencial: Actualización del estado actual con el reloj
    process(clk, reset)
    begin
        if reset = '1' then
            current_state <= S0; -- Retorno al estado inicial en reset
        elsif rising_edge(clk) then
            current_state <= next_state;
        end if;
    end process;

    -- Proceso combinacional: Lógica de próximo estado y salida
    process(current_state, X)
    begin
        -- Valor por defecto de la salida
        Z <= '0'; 
        
        case current_state is
            when S0 =>
                if X = '1' then next_state <= S1; else next_state <= S0; end if;
            when S1 =>
                if X = '0' then next_state <= S2; else next_state <= S1; end if;
            when S2 =>
                if X = '1' then next_state <= S3; else next_state <= S0; end if;
            when S3 =>
                if X = '1' then next_state <= S4; else next_state <= S2; end if;
            when S4 =>
                if X = '0' then next_state <= S5; else next_state <= S1; end if;
            when S5 =>
                if X = '1' then next_state <= S6; else next_state <= S0; end if;
            when S6 =>
                if X = '0' then next_state <= S7; else next_state <= S4; end if;
            when S7 =>
                Z <= '1'; -- La salida se pone en ALTO al completar la secuencia
                -- Lógica para secuencias superpuestas (traslapadas)
                if X = '1' then next_state <= S3; else next_state <= S0; end if;
            when others =>
                next_state <= S0;
        end case;
    end process;
	 process(current_state)
    begin
     case current_state is
        when S0 => debug_state <= "000";
        when S1 => debug_state <= "001";
        when S2 => debug_state <= "010";
        when S3 => debug_state <= "011";
        when S4 => debug_state <= "100";
        when S5 => debug_state <= "101";
        when S6 => debug_state <= "110";
        when S7 => debug_state <= "111";
    end case;
end process;

end Behavioral;
