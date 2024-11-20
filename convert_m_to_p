function convert_m_to_p(folder_path)
    % Get a list of all .m files in the specified folder
    m_files = dir(fullfile(folder_path, '*.m'));
    
    % Create a subfolder for the .p files
    p_folder = fullfile(folder_path, 'p_files');
    mkdir(p_folder);

    % Convert each .m file to .p and move it to the p_files folder
    for i = 1:length(m_files)
        m_file = fullfile(folder_path, m_files(i).name);
        
        % Generate the .p file in place
        pcode(m_file, '-inplace');
        
        % Rename and move the .p file to the p_files folder
        p_file_name = strrep(m_files(i).name, '.m', '.p');
        movefile(fullfile(folder_path, p_file_name), p_folder);
    end

    % Verify and move remaining .p files to the p_files folder
    p_files = dir(fullfile(folder_path, '*.p'));
    for i = 1:length(p_files)
        src_file = fullfile(folder_path, p_files(i).name);
        dest_file = fullfile(p_folder, p_files(i).name);
        movefile(src_file, dest_file);
    end
end
