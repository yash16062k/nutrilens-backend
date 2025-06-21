package com.nutrilens.nutrilens_backend.service;

import org.springframework.beans.factory.annotation.Value;
import org.springframework.stereotype.Service;
import org.springframework.web.client.RestTemplate;

import java.util.*;

@Service
public class NutritionService {

    @Value("${nutritionix.app.id}")
    private String appId;

    @Value("${nutritionix.app.key}")
    private String appKey;

    private final RestTemplate restTemplate = new RestTemplate();

    public Map<String, Object> lookup(String itemName) {
        String url = "https://trackapi.nutritionix.com/v2/natural/nutrients";

        // Set headers
        org.springframework.http.HttpHeaders headers = new org.springframework.http.HttpHeaders();
        headers.set("x-app-id", appId);
        headers.set("x-app-key", appKey);
        headers.set("Content-Type", "application/json");

        // Set body
        Map<String, String> body = Map.of("query", itemName);

        // Create request entity
        org.springframework.http.HttpEntity<Map<String, String>> entity =
                new org.springframework.http.HttpEntity<>(body, headers);

        // Make request and return response
        return restTemplate.postForObject(url, entity, Map.class);
    }
}
